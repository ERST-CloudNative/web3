## 运行Fabric应用程序

本节主要介绍Fabric 应用程序如何与已部署的区块链网络进行交互。这里使用使用 Fabric Gateway 客户端 API 构建的示例程序来调用智能合约。

关于资产转让示例主要演示如何创建、更新和查询资产，主要有以下两个部分组成：
- 示例应用程序：向区块链网络发起请求，调用智能合约中实现的交易，该应用程序代码位于fabric-samples目录中

```
asset-transfer-basic/application-gateway-typescript
```

- 智能合约：实现与账本交互的交易。智能合约位于fabric-samples目录中

```
asset-transfer-basic/chaincode-(typescript, go, java)
```

https://hyperledger-fabric.readthedocs.io/en/latest/_images/AppConceptsOverview.png

关于本节内容主要有两个部分：
- 建立区块链网络。 应用程序需要与区块链网络进行交互，因此我们将启动一个基本网络并为我们的应用程序部署智能合约。
- 运行示例应用程序以与智能合约交互。 应用程序将使用 `assetTransfer` 智能合约来创建、查询和更新账本上的资产。

#### 启动区块链网络

在启动新网络之前关闭正在运行的网络，以确保您从一个空的账本开始。

这里将部署具有两个对等点、一个排序服务和三个证书颁发机构（Orderer、Org1、Org2）的 Fabric 测试网络。不使用 cryptogen 工具，而是使用证书颁发机构启动测试网络，因此有了标志-ca。此外，当证书颁发机构启动时，会引导组织管理员用户注册。

```
[root@hy test-network]# ./network.sh up createChannel -c mychannel -ca
```

查看启动的Fabric测试网络

```
[root@hy test-network]# docker ps
CONTAINER ID   IMAGE                               COMMAND                  CREATED          STATUS          PORTS                                                                                                                             NAMES
374fbbf2d9ac   hyperledger/fabric-tools:latest     "/bin/bash"              16 seconds ago   Up 14 seconds                                                                                                                                     cli
b562cae99e8b   hyperledger/fabric-peer:latest      "peer node start"        16 seconds ago   Up 15 seconds   0.0.0.0:7051->7051/tcp, :::7051->7051/tcp, 0.0.0.0:9444->9444/tcp, :::9444->9444/tcp                                              peer0.org1.example.com
e8d8646f1f4b   hyperledger/fabric-peer:latest      "peer node start"        16 seconds ago   Up 14 seconds   0.0.0.0:9051->9051/tcp, :::9051->9051/tcp, 7051/tcp, 0.0.0.0:9445->9445/tcp, :::9445->9445/tcp                                    peer0.org2.example.com
cee0752ac996   hyperledger/fabric-orderer:latest   "orderer"                16 seconds ago   Up 14 seconds   0.0.0.0:7050->7050/tcp, :::7050->7050/tcp, 0.0.0.0:7053->7053/tcp, :::7053->7053/tcp, 0.0.0.0:9443->9443/tcp, :::9443->9443/tcp   orderer.example.com
77ef16dfc815   hyperledger/fabric-ca:latest        "sh -c 'fabric-ca-se…"   22 seconds ago   Up 21 seconds   0.0.0.0:9054->9054/tcp, :::9054->9054/tcp, 7054/tcp, 0.0.0.0:19054->19054/tcp, :::19054->19054/tcp                                ca_orderer
ece83d570509   hyperledger/fabric-ca:latest        "sh -c 'fabric-ca-se…"   22 seconds ago   Up 20 seconds   0.0.0.0:7054->7054/tcp, :::7054->7054/tcp, 0.0.0.0:17054->17054/tcp, :::17054->17054/tcp                                          ca_org1
5a5a531ed44a   hyperledger/fabric-ca:latest        "sh -c 'fabric-ca-se…"   22 seconds ago   Up 20 seconds   0.0.0.0:8054->8054/tcp, :::8054->8054/tcp, 7054/tcp, 0.0.0.0:18054->18054/tcp, :::18054->18054/tcp                                ca_org2
```

#### 部署智能合约

```
[root@hy test-network]# ./network.sh deployCC -ccn basic -ccp ../asset-transfer-basic/chaincode-go/ -ccl go
```

#### 准备示例应用程序

下载依赖库

```
[root@hy test-network]# cd ../asset-transfer-basic/application-gateway-go/
[root@hy application-gateway-go]# GO111MODULE=on go mod vendor
```

#### 运行示例应用程序

前面启动 Fabric 测试网络时，使用证书颁发机构创建了多个身份。其中包括每个组织的用户身份。该应用程序将使用这些用户身份之一的凭据与区块链网络进行交易。

```
[root@hy application-gateway-go]# go run .

--> Submit Transaction: InitLedger, function creates the initial set of assets on the ledger
*** Transaction committed successfully

--> Evaluate Transaction: GetAllAssets, function returns all the current assets on the ledger
*** Result:[
  {
    "AppraisedValue": 300,
    "Color": "blue",
    "ID": "asset1",
    "Owner": "Tomoko",
    "Size": 5
  },
  {
    "AppraisedValue": 400,
    "Color": "red",
    "ID": "asset2",
    "Owner": "Brad",
    "Size": 5
  },
  {
    "AppraisedValue": 500,
    "Color": "green",
    "ID": "asset3",
    "Owner": "Jin Soo",
    "Size": 10
  },
  {
    "AppraisedValue": 600,
    "Color": "yellow",
    "ID": "asset4",
    "Owner": "Max",
    "Size": 10
  },
  {
    "AppraisedValue": 700,
    "Color": "black",
    "ID": "asset5",
    "Owner": "Adriana",
    "Size": 15
  },
  {
    "AppraisedValue": 800,
    "Color": "white",
    "ID": "asset6",
    "Owner": "Michel",
    "Size": 15
  },
  {
    "AppraisedValue": 900,
    "Color": "red",
    "ID": "asset7",
    "Owner": "Oracle",
    "Size": 20
  }
]

--> Submit Transaction: CreateAsset, creates new asset with ID, Color, Size, Owner and AppraisedValue arguments
*** Transaction committed successfully

--> Evaluate Transaction: ReadAsset, function returns asset attributes
*** Result:{
  "AppraisedValue": 1300,
  "Color": "yellow",
  "ID": "asset1698224408675",
  "Owner": "Tom",
  "Size": 5
}

--> Async Submit Transaction: TransferAsset, updates existing asset owner
*** Successfully submitted transaction to transfer ownership from Tom to Mark.
*** Waiting for transaction commit.
*** Transaction committed successfully

--> Submit Transaction: UpdateAsset asset70, asset70 does not exist and should return an error
*** Successfully caught the error:
Endorse error for transaction 7998b9977c3e0e1783e6db2f092003c6f06459ad325eaed03db63d9df7a82a39 with gRPC status Aborted: rpc error: code = Aborted desc = failed to endorse transaction, see attached details for more info
Error Details:
- address: peer0.org1.example.com:7051, mspId: Org1MSP, message: chaincode response 500, the asset asset70 does not exist
```

#### 源码结构

##### 1. 建立与网关的gRPC连接

客户端应用程序与 Fabric Gateway 服务建立gRPC连接，该连接将用于与区块链网络进行交易。为此，它只需要 Fabric Gateway 的端点地址，并且如果配置为使用 TLS，则还需要适当的 TLS 证书。在此示例中，网关端点地址是提供 Fabric Gateway 服务的对等方的地址。

为了成功建立 TLS 连接，客户端使用的端点地址必须与网关 TLS 证书中的地址匹配。由于客户端通过某个localhost地址访问网关的 Docker 容器，因此指定了 gRPC 选项来强制将此端点地址解释为网关配置的主机名。

```
const (
        mspID        = "Org1MSP"
        cryptoPath   = "../../test-network/organizations/peerOrganizations/org1.example.com"
        certPath     = cryptoPath + "/users/User1@org1.example.com/msp/signcerts/cert.pem"
        keyPath      = cryptoPath + "/users/User1@org1.example.com/msp/keystore/"
        tlsCertPath  = cryptoPath + "/peers/peer0.org1.example.com/tls/ca.crt"
        peerEndpoint = "localhost:7051"
        gatewayPeer  = "peer0.org1.example.com"
)

// newGrpcConnection creates a gRPC connection to the Gateway server.
func newGrpcConnection() *grpc.ClientConn {
        certificate, err := loadCertificate(tlsCertPath)
        if err != nil {
                panic(err)
        }

        certPool := x509.NewCertPool()
        certPool.AddCert(certificate)
        transportCredentials := credentials.NewClientTLSFromCert(certPool, gatewayPeer)

        connection, err := grpc.Dial(peerEndpoint, grpc.WithTransportCredentials(transportCredentials))
        if err != nil {
                panic(fmt.Errorf("failed to create gRPC connection: %w", err))
        }

        return connection
}


```

#### 2. 创建Gateway连接

然后，应用程序创建一个Gateway连接，用于访问Fabric Gateway 可访问的任何资源，并随后智能合约会部署到这些网络。Gateway连接需要有三个要求：
- 与 Fabric Gateway 的 gRPC 连接。
- 用于与网络进行交易的客户端身份。
- 签名实现用于为客户端身份生成数字签名。

示例应用程序使用 Org1 用户的 X.509 证书作为客户端身份，并使用基于该用户私钥的签名实现。

```
...
        // The gRPC client connection should be shared by all Gateway connections to this endpoint
        clientConnection := newGrpcConnection()
        defer clientConnection.Close()

        id := newIdentity()
        sign := newSign()

        // Create a Gateway connection for a specific client identity
        gw, err := client.Connect(
                id,
                client.WithSign(sign),
                client.WithClientConnection(clientConnection),
                // Default timeouts for different gRPC calls
                client.WithEvaluateTimeout(5*time.Second),
                client.WithEndorseTimeout(15*time.Second),
                client.WithSubmitTimeout(5*time.Second),
                client.WithCommitStatusTimeout(1*time.Minute),
        )
...


// newIdentity creates a client identity for this Gateway connection using an X.509 certificate.
func newIdentity() *identity.X509Identity {
        certificate, err := loadCertificate(certPath)
        if err != nil {
                panic(err)
        }

        id, err := identity.NewX509Identity(mspID, certificate)
        if err != nil {
                panic(err)
        }

        return id
}

// newSign creates a function that generates a digital signature from a message digest using a private key.
func newSign() identity.Sign {
        files, err := os.ReadDir(keyPath)
        if err != nil {
                panic(fmt.Errorf("failed to read private key directory: %w", err))
        }
        privateKeyPEM, err := os.ReadFile(path.Join(keyPath, files[0].Name()))

        if err != nil {
                panic(fmt.Errorf("failed to read private key file: %w", err))
        }

        privateKey, err := identity.PrivateKeyFromPEM(privateKeyPEM)
        if err != nil {
                panic(err)
        }

        sign, err := identity.NewPrivateKeySign(privateKey)
        if err != nil {
                panic(err)
        }

        return sign
}

```

#### 3. 访问要调用的智能合约

示例应用程序使用该Gateway连接来获取对网络的引用，然后获取该网络上已部署链码内的智能合约。

```
network := gw.GetNetwork(channelName)
contract := network.GetContract(chaincodeName)
```

#### 4. 用样本资产填充账本

链码包初始部署后，账本立即为空。应用程序使用`submitTransaction()`调用`InitLedger`交易函数，该函数用一些示例资产填充分类账。`submitTransaction()`将用来：
- 批准交易提案。
- 将背书的交易提交给订购服务。
- 等待事务提交，更新账本状态。

示例应用程序InitLedger调用：

```
// This type of transaction would typically only be run once by an application the first time it was started after its
// initial deployment. A new version of the chaincode deployed later would likely not need to run an "init" function.
func initLedger(contract *client.Contract) {
        fmt.Printf("\n--> Submit Transaction: InitLedger, function creates the initial set of assets on the ledger \n")

        _, err := contract.SubmitTransaction("InitLedger")
        if err != nil {
                panic(fmt.Errorf("failed to submit transaction: %w", err))
        }

        fmt.Printf("*** Transaction committed successfully\n")
}

```

#### 4. 调用交易函数读写资产

现在，应用程序已准备好执行业务逻辑，通过调用智能合约上的交易功能来查询、创建附加资产以及修改分类账上的资产。

4.1 查询所有资产

应用程序通过`evaluateTransaction()`执行只读事务调用来查询分类帐。 交易不会发送到排序服务，也不会发生账本更新。

```
// Evaluate a transaction to query ledger state.
func getAllAssets(contract *client.Contract) {
        fmt.Println("\n--> Evaluate Transaction: GetAllAssets, function returns all the current assets on the ledger")

        evaluateResult, err := contract.EvaluateTransaction("GetAllAssets")
        if err != nil {
                panic(fmt.Errorf("failed to evaluate transaction: %w", err))
        }
        result := formatJSON(evaluateResult)

        fmt.Printf("*** Result:%s\n", result)
}
```

4.2 创建新资产

```
// Submit a transaction synchronously, blocking until it has been committed to the ledger.
func createAsset(contract *client.Contract) {
        fmt.Printf("\n--> Submit Transaction: CreateAsset, creates new asset with ID, Color, Size, Owner and AppraisedValue arguments \n")

        _, err := contract.SubmitTransaction("CreateAsset", assetId, "yellow", "5", "Tom", "1300")
        if err != nil {
                panic(fmt.Errorf("failed to submit transaction: %w", err))
        }

        fmt.Printf("*** Transaction committed successfully\n")
}

```

4.3 更新资产

示例应用程序提交交易以转移新创建资产的所有权。这次使用`submitAsync()`调用交易，它在成功将背书交易提交到排序服务后返回，而不是等到交易提交到分类帐。这允许应用程序在等待提交事务结果的同时使用事务结果执行工作。

```
// Submit transaction asynchronously, blocking until the transaction has been sent to the orderer, and allowing
// this thread to process the chaincode response (e.g. update a UI) without waiting for the commit notification
func transferAssetAsync(contract *client.Contract) {
        fmt.Printf("\n--> Async Submit Transaction: TransferAsset, updates existing asset owner")

        submitResult, commit, err := contract.SubmitAsync("TransferAsset", client.WithArguments(assetId, "Mark"))
        if err != nil {
                panic(fmt.Errorf("failed to submit transaction asynchronously: %w", err))
        }

        fmt.Printf("\n*** Successfully submitted transaction to transfer ownership from %s to Mark. \n", string(submitResult))
        fmt.Println("*** Waiting for transaction commit.")

        if commitStatus, err := commit.Status(); err != nil {
                panic(fmt.Errorf("failed to get commit status: %w", err))
        } else if !commitStatus.Successful {
                panic(fmt.Errorf("transaction %s failed to commit with status: %d", commitStatus.TransactionID, int32(commitStatus.Code)))
        }

        fmt.Printf("*** Transaction committed successfully\n")
}

```


4.4 查询更新后的资产

示例应用程序评估对所转移资产的查询，显示它是使用所描述的属性创建的，然后随后转移给新所有者。

```
func readAssetByID(contract *client.Contract) {
        fmt.Printf("\n--> Evaluate Transaction: ReadAsset, function returns asset attributes\n")

        evaluateResult, err := contract.EvaluateTransaction("ReadAsset", assetId)
        if err != nil {
                panic(fmt.Errorf("failed to evaluate transaction: %w", err))
        }
        result := formatJSON(evaluateResult)

        fmt.Printf("*** Result:%s\n", result)
}

```

4.5 处理交易错误

最后部分演示了提交事务时出现的错误。在此示例中，应用程序尝试提交`UpdateAsset`交易，但指定的资产 `ID` 不存在。交易函数返回错误响应，调用`submitTransaction()`失败。

```
// Submit transaction, passing in the wrong number of arguments ,expected to throw an error containing details of any error responses from the smart contract.
func exampleErrorHandling(contract *client.Contract) {
        fmt.Println("\n--> Submit Transaction: UpdateAsset asset70, asset70 does not exist and should return an error")

        _, err := contract.SubmitTransaction("UpdateAsset", "asset70", "blue", "5", "Tomoko", "300")
        if err == nil {
                panic("******** FAILED to return an error")
        }

        fmt.Println("*** Successfully caught the error:")

        switch err := err.(type) {
        case *client.EndorseError:
                fmt.Printf("Endorse error for transaction %s with gRPC status %v: %s\n", err.TransactionID, status.Code(err), err)
        case *client.SubmitError:
                fmt.Printf("Submit error for transaction %s with gRPC status %v: %s\n", err.TransactionID, status.Code(err), err)
        case *client.CommitStatusError:
                if errors.Is(err, context.DeadlineExceeded) {
                        fmt.Printf("Timeout waiting for transaction %s commit status: %s", err.TransactionID, err)
                } else {
                        fmt.Printf("Error obtaining commit status for transaction %s with gRPC status %v: %s\n", err.TransactionID, status.Code(err), err)
                }
        case *client.CommitError:
                fmt.Printf("Transaction %s failed to commit with status %d: %s\n", err.TransactionID, int32(err.Code), err)
        default:
                panic(fmt.Errorf("unexpected error type %T: %w", err, err))
        }

        // Any error that originates from a peer or orderer node external to the gateway will have its details
        // embedded within the gRPC status error. The following code shows how to extract that.
        statusErr := status.Convert(err)

        details := statusErr.Details()
        if len(details) > 0 {
                fmt.Println("Error Details:")

                for _, detail := range details {
                        switch detail := detail.(type) {
                        case *gateway.ErrorDetail:
                                fmt.Printf("- address: %s, mspId: %s, message: %s\n", detail.Address, detail.MspId, detail.Message)
                        }
                }
        }
}

```










