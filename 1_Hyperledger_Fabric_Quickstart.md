## Hyperledger Fabric QuickStart

### 环境准备

虚拟机配置

```
OS: Oracle Linux 8
VM: 2 OCPU/8 GB/50GB
```

安装所需软件

```
# 安装git
yum install -y git

# 安装jq
dnf install jq -y

# 安装docker
yum remove docker docker-common docker-selinux docker-engine -y
dnf install –y dnf-utils zip unzip
dnf install -y dnf-utils zip unzip
dnf config-manager –add-repo=https://download.docker.com/linux/centos/docker-ce.repo
dnf config-manager --add-repo=https://download.docker.com/linux/centos/docker-ce.repo
dnf install -y docker-ce --nobest
systemctl enable docker.service --now

# 安装docker-compose

curl -L https://github.com/docker/compose/releases/download/v2.21.0/docker-compose-linux-x86_64 -o /usr/bin/docker-compose
chmod +x /usr/bin/docker-compose
docker-compose --version

# 安装golang

wget https://go.dev/dl/go1.20.10.linux-amd64.tar.gz
tar -zxvf go1.20.10.linux-amd64.tar.gz -C /usr/local/bin/

## 配置环境变量/etc/profile
export GOROOT=/usr/local/bin/go/
export PATH=$GOROOT/bin:$PATH
export GOPATH=$HOME/go
export PATH=$PATH:$GOPATH/bin

## 使配置生效
source /etc/profile

# 验证安装是否成功
go version
```

### Fabric测试体验

#### 启动Fabric测试网络

```
[root@hy ~]# mkdir -p go/src/github.com/b43646/
[root@hy ~]# cd go/src/github.com/b43646/
[root@hy b43646]# curl -sSLO https://raw.githubusercontent.com/hyperledger/fabric/main/scripts/install-fabric.sh && chmod +x install-fabric.sh
# 拉取Docker 容器镜像并克隆示例代码
[root@hy b43646]# ./install-fabric.sh docker samples binary

===> List out hyperledger images
hyperledger/fabric-ca        1.5       0f07bbee6fb8   8 weeks ago    223MB
hyperledger/fabric-ca        1.5.7     0f07bbee6fb8   8 weeks ago    223MB
hyperledger/fabric-ca        latest    0f07bbee6fb8   8 weeks ago    223MB
hyperledger/fabric-tools     2.5       b2f3af4021be   2 months ago   551MB
hyperledger/fabric-tools     2.5.4     b2f3af4021be   2 months ago   551MB
hyperledger/fabric-tools     latest    b2f3af4021be   2 months ago   551MB
hyperledger/fabric-peer      2.5       4f8d1b54d8b0   2 months ago   135MB
hyperledger/fabric-peer      2.5.4     4f8d1b54d8b0   2 months ago   135MB
hyperledger/fabric-peer      latest    4f8d1b54d8b0   2 months ago   135MB
hyperledger/fabric-orderer   2.5       7a73187b5c49   2 months ago   106MB
hyperledger/fabric-orderer   2.5.4     7a73187b5c49   2 months ago   106MB
hyperledger/fabric-orderer   latest    7a73187b5c49   2 months ago   106MB
hyperledger/fabric-ccenv     2.5       6dac93f94c87   2 months ago   656MB
hyperledger/fabric-ccenv     2.5.4     6dac93f94c87   2 months ago   656MB
hyperledger/fabric-ccenv     latest    6dac93f94c87   2 months ago   656MB
hyperledger/fabric-baseos    2.5       3854817b987d   2 months ago   122MB
hyperledger/fabric-baseos    2.5.4     3854817b987d   2 months ago   122MB
hyperledger/fabric-baseos    latest    3854817b987d   2 months ago   122MB

# 安装指定版本的fabric二进制文件
[root@hy b43646]# ./install-fabric.sh --fabric-version 2.5.0 binary

Pull Hyperledger Fabric binaries

===> Downloading version 2.5.0 platform specific fabric binaries
===> Downloading:  https://github.com/hyperledger/fabric/releases/download/v2.5.0/hyperledger-fabric-linux-amd64-2.5.0.tar.gz
...
===> Downloading version 1.5.7 platform specific fabric-ca-client binary
===> Downloading:  https://github.com/hyperledger/fabric-ca/releases/download/v1.5.7/hyperledger-fabric-ca-linux-amd64-1.5.7.tar.gz
===> Will unpack to: fabric-samples
...
==> Done.

[root@hy b43646]# cd fabric-samples/test-network

# 运行fabric网络
[root@hy test-network]# ./network.sh up
```

#### 查看Fabric测试网络组成

通过命令行可以查看网络组成中包括：两个pee节点+一个order节点

peer节点在Fabric中被称为主节点模块，主要负责存储区块链数据、运行维护链码、提供对外服务接口等作用，这里每个peer节点对应一个组织，分别为org1和org2
orderer是一种特殊的peer节点，负责排序服务，保持peer之间账本的一致性；

```
[root@hy test-network]# docker ps
CONTAINER ID   IMAGE                               COMMAND             CREATED         STATUS         PORTS                                                                                                                             NAMES
bf1f99c73f3a   hyperledger/fabric-tools:latest     "/bin/bash"         3 minutes ago   Up 3 minutes                                                                                                                                     cli
de35c93780ea   hyperledger/fabric-orderer:latest   "orderer"           3 minutes ago   Up 3 minutes   0.0.0.0:7050->7050/tcp, :::7050->7050/tcp, 0.0.0.0:7053->7053/tcp, :::7053->7053/tcp, 0.0.0.0:9443->9443/tcp, :::9443->9443/tcp   orderer.example.com
5e4cbea81eae   hyperledger/fabric-peer:latest      "peer node start"   3 minutes ago   Up 3 minutes   0.0.0.0:9051->9051/tcp, :::9051->9051/tcp, 7051/tcp, 0.0.0.0:9445->9445/tcp, :::9445->9445/tcp                                    peer0.org2.example.com
3b68dd30458e   hyperledger/fabric-peer:latest      "peer node start"   3 minutes ago   Up 3 minutes   0.0.0.0:7051->7051/tcp, :::7051->7051/tcp, 0.0.0.0:9444->9444/tcp, :::9444->9444/tcp                                              peer0.org1.example.com
```

#### 创建通道

目前Fabric网络上已经运行了对等节点和排序节点，接下来，可以使用脚本为 Org1 和 Org2 之间的事务创建 Fabric 通道。通道是特定网络成员之间通信的私有层。通道只能由受邀加入通道的组织使用，并且对网络的其他成员不可见。每个通道都有一个单独的区块链账本。受邀的组织将其peer加入通道，以存储通道分类账并验证通道上的交易。

```
# 默认通道名称：mychannel
[root@hy test-network]# ./network.sh createChannel
...
Channel 'mychannel' created
Joining org1 peer to the channel...
...
Joining org2 peer to the channel...
...
{
        "approvals": {
                "Org1MSP": true,
                "Org2MSP": true
        }
}
...
Committed chaincode definition for chaincode 'basic' on channel 'mychannel':
Version: 1.0.1, Sequence: 1, Endorsement Plugin: escc, Validation Plugin: vscc, Approvals: [Org1MSP: true, Org2MSP: true]
Query chaincode definition successful on peer0.org2 on channel 'mychannel'
Chaincode initialization is not required
```

#### 在通道上启动链码

创建通道后，可以开始使用智能合约与通道账本进行交互。智能合约包含管理区块链分类账上资产的业务逻辑。网络成员运行的应用程序可以调用智能合约在账本上创建资产，以及更改和转移这些资产。应用程序还查询智能合约以读取账本上的数据。

在 Fabric 中，智能合约以称为链代码的包部署在网络上。链代码安装在组织的对等点上，然后部署到通道，然后可以在通道中使用它来背书交易并与区块链分类账交互。在将链码部署到通道之前，通道成员需要就建立链码治理的链码定义达成一致。当所需数量的组织同意时，可以将链码定义提交到通道，并且链码就可以使用了。

```
[root@hy test-network]# ./network.sh deployCC -ccn basic -ccp ../asset-transfer-basic/chaincode-go -ccl go
```

#### 与Fabric测试网络交互

初始化账本

```
[root@hy test-network]# export PATH=${PWD}/../bin:$PATH
[root@hy test-network]# export CORE_PEER_TLS_ENABLED=true
[root@hy test-network]# export CORE_PEER_LOCALMSPID="Org1MSP"
[root@hy test-network]# export CORE_PEER_TLS_ROOTCERT_FILE=${PWD}/organizations/peerOrganizations/org1.example.com/peers/peer0.org1.example.com/tls/ca.crt
[root@hy test-network]# export CORE_PEER_MSPCONFIGPATH=${PWD}/organizations/peerOrganizations/org1.example.com/users/Admin@org1.example.com/msp
[root@hy test-network]# export CORE_PEER_ADDRESS=localhost:7051
[root@hy test-network]# export FABRIC_CFG_PATH=$PWD/../config/

# 初始化命令：InitLedger
[root@hy test-network]# peer chaincode invoke -o localhost:7050 --ordererTLSHostnameOverride orderer.example.com --tls --cafile "${PWD}/organizations/ordererOrganizations/example.com/orderers/orderer.example.com/msp/tlscacerts/tlsca.example.com-cert.pem" -C mychannel -n basic --peerAddresses localhost:7051 --tlsRootCertFiles "${PWD}/organizations/peerOrganizations/org1.example.com/peers/peer0.org1.example.com/tls/ca.crt" --peerAddresses localhost:9051 --tlsRootCertFiles "${PWD}/organizations/peerOrganizations/org2.example.com/peers/peer0.org2.example.com/tls/ca.crt" -c '{"function":"InitLedger","Args":[]}'

2023-10-25 06:58:24.346 GMT 0001 INFO [chaincodeCmd] chaincodeInvokeOrQuery -> Chaincode invoke successful. result: status:200
```

获取已添加到通道分类帐的资产列表

```
[root@hy test-network]# peer chaincode query -C mychannel -n basic -c '{"Args":["GetAllAssets"]}'
[{"AppraisedValue":300,"Color":"blue","ID":"asset1","Owner":"Tomoko","Size":5},{"AppraisedValue":400,"Color":"red","ID":"asset2","Owner":"Brad","Size":5},{"AppraisedValue":500,"Color":"green","ID":"asset3","Owner":"Jin Soo","Size":10},{"AppraisedValue":600,"Color":"yellow","ID":"asset4","Owner":"Max","Size":10},{"AppraisedValue":700,"Color":"black","ID":"asset5","Owner":"Adriana","Size":15},{"AppraisedValue":800,"Color":"white","ID":"asset6","Owner":"Michel","Size":15}]
```

执行资产转移操作

```
[root@hy test-network]# peer chaincode invoke -o localhost:7050 --ordererTLSHostnameOverride orderer.example.com --tls --cafile "${PWD}/organizations/ordererOrganizations/example.com/orderers/orderer.example.com/msp/tlscacerts/tlsca.example.com-cert.pem" -C mychannel -n basic --peerAddresses localhost:7051 --tlsRootCertFiles "${PWD}/organizations/peerOrganizations/org1.example.com/peers/peer0.org1.example.com/tls/ca.crt" --peerAddresses localhost:9051 --tlsRootCertFiles "${PWD}/organizations/peerOrganizations/org2.example.com/peers/peer0.org2.example.com/tls/ca.crt" -c '{"function":"TransferAsset","Args":["asset6","Christopher"]}'

2023-10-25 07:01:32.806 GMT 0001 INFO [chaincodeCmd] chaincodeInvokeOrQuery -> Chaincode invoke successful. result: status:200 payload:"Michel"
```

验证资产转移操作是否成功(owner是否改变)

```
[root@hy test-network]# export CORE_PEER_TLS_ENABLED=true
[root@hy test-network]# export CORE_PEER_LOCALMSPID="Org2MSP"
[root@hy test-network]# export CORE_PEER_TLS_ROOTCERT_FILE=${PWD}/organizations/peerOrganizations/org2.example.com/peers/peer0.org2.example.com/tls/ca.crt
[root@hy test-network]# export CORE_PEER_MSPCONFIGPATH=${PWD}/organizations/peerOrganizations/org2.example.com/users/Admin@org2.example.com/msp
[root@hy test-network]# export CORE_PEER_ADDRESS=localhost:9051

[root@hy test-network]# peer chaincode query -C mychannel -n basic -c '{"Args":["ReadAsset","asset6"]}'

{"AppraisedValue":800,"Color":"white","ID":"asset6","Owner":"Christopher","Size":15}
```

#### 关闭Fabric测试网络

```
[root@hy test-network]# ./network.sh down

```
