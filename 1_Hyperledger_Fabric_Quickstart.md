

```
[root@hy ~]# cd go/src/github.com/b43646/
[root@hy b43646]# ls
[root@hy b43646]# curl -sSLO https://raw.githubusercontent.com/hyperledger/fabric/main/scripts/install-fabric.sh && chmod +x install-fabric.sh
[root@hy b43646]# ./install-fabric.sh -h
Usage: ./install-fabric.sh [-f|--fabric-version <arg>] [-c|--ca-version <arg>] <comp-1> [<comp-2>] ... [<comp-n>] ...
        <comp> Component to install, one or more of  docker | binary | samples | podman  First letter of component also accepted; If none specified docker | binary | samples is assumed
        -f, --fabric-version: FabricVersion (default: '2.5.4')
        -c, --ca-version: Fabric CA Version (default: '1.5.7')
[root@hy b43646]# ./install-fabric.sh docker samples binary

Clone hyperledger/fabric-samples repo

===> Cloning hyperledger/fabric-samples repo
Cloning into 'fabric-samples'...
remote: Enumerating objects: 12780, done.
remote: Counting objects: 100% (812/812), done.
remote: Compressing objects: 100% (481/481), done.
remote: Total 12780 (delta 372), reused 595 (delta 282), pack-reused 11968
Receiving objects: 100% (12780/12780), 22.85 MiB | 21.84 MiB/s, done.
Resolving deltas: 100% (6826/6826), done.
fabric-samples v2.5.4 does not exist, defaulting to main. fabric-samples main branch is intended to work with recent versions of fabric.

Pull Hyperledger Fabric binaries

===> Downloading version 2.5.4 platform specific fabric binaries
===> Downloading:  https://github.com/hyperledger/fabric/releases/download/v2.5.4/hyperledger-fabric-linux-amd64-2.5.4.tar.gz
===> Will unpack to: /root/go/src/github.com/b43646/fabric-samples
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
100 99.3M  100 99.3M    0     0  32.7M      0  0:00:03  0:00:03 --:--:-- 37.9M
==> Done.
===> Downloading version 1.5.7 platform specific fabric-ca-client binary
===> Downloading:  https://github.com/hyperledger/fabric-ca/releases/download/v1.5.7/hyperledger-fabric-ca-linux-amd64-1.5.7.tar.gz
===> Will unpack to: /root/go/src/github.com/b43646/fabric-samples
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
100 34.0M  100 34.0M    0     0  20.1M      0  0:00:01  0:00:01 --:--:-- 25.5M
==> Done.

Pull Hyperledger Fabric docker images

FABRIC_IMAGES: peer orderer ccenv tools baseos
===> Pulling fabric Images
====>  docker.io/hyperledger/fabric-peer:2.5.4
2.5.4: Pulling from hyperledger/fabric-peer
01085d60b3a6: Pull complete
5920bb1ab585: Pull complete
0c13247db338: Pull complete
f1ebf2febfff: Pull complete
7ba246813ff2: Pull complete
20e090879749: Pull complete
Digest: sha256:c2e735a3cb8250c47ed3589294b3f0c078004ec001b949710f334736651e106d
Status: Downloaded newer image for hyperledger/fabric-peer:2.5.4
docker.io/hyperledger/fabric-peer:2.5.4
====>  docker.io/hyperledger/fabric-orderer:2.5.4
2.5.4: Pulling from hyperledger/fabric-orderer
01085d60b3a6: Already exists
0ec39628d119: Pull complete
c9ef912f2449: Pull complete
5f267c8c968e: Pull complete
54a738441be6: Pull complete
d6c2bf9dde2f: Pull complete
Digest: sha256:1a7144705b435062f4be2886de98d0408165cf51326ec721c3f58b40bf8bf139
Status: Downloaded newer image for hyperledger/fabric-orderer:2.5.4
docker.io/hyperledger/fabric-orderer:2.5.4
====>  docker.io/hyperledger/fabric-ccenv:2.5.4
2.5.4: Pulling from hyperledger/fabric-ccenv
01085d60b3a6: Already exists
0a0dd1fd96cb: Pull complete
6511dcb32b75: Pull complete
a1ad41013466: Pull complete
7b4bed92341a: Pull complete
9c0ab6ce970a: Pull complete
d79fd538cbf0: Pull complete
Digest: sha256:b7d312c0f8d4530c6ff4b3ef7277f0338f486d0b617c3012415a32308cbc2254
Status: Downloaded newer image for hyperledger/fabric-ccenv:2.5.4
docker.io/hyperledger/fabric-ccenv:2.5.4
====>  docker.io/hyperledger/fabric-tools:2.5.4
2.5.4: Pulling from hyperledger/fabric-tools
01085d60b3a6: Already exists
367f9186226c: Pull complete
b47f6a4ae6bc: Pull complete
b5933c87679e: Pull complete
77b2bdbf772c: Pull complete
b2d9526a33e2: Pull complete
Digest: sha256:b3aea8173802186244663334b4196c415cb267d77ea8c617fdd30652c5a732c4
Status: Downloaded newer image for hyperledger/fabric-tools:2.5.4
docker.io/hyperledger/fabric-tools:2.5.4
====>  docker.io/hyperledger/fabric-baseos:2.5.4
2.5.4: Pulling from hyperledger/fabric-baseos
01085d60b3a6: Already exists
cc16ebc66c1e: Pull complete
cfb66da0a833: Pull complete
daa87923bf69: Pull complete
Digest: sha256:cab2ed27ed8d27e4cacde447a1de51884f0bd9e103a6119e74521e1b90b6d106
Status: Downloaded newer image for hyperledger/fabric-baseos:2.5.4
docker.io/hyperledger/fabric-baseos:2.5.4
===> Pulling fabric ca Image
====>  docker.io/hyperledger/fabric-ca:1.5.7
1.5.7: Pulling from hyperledger/fabric-ca
edaedc954fb5: Pull complete
793f509072c1: Pull complete
40231dd4f3a4: Pull complete
5799c17ab94e: Pull complete
Digest: sha256:db814e013fc29f94f75a5df6e3920c08a4e96e53a079152df2ffa99e6db24861
Status: Downloaded newer image for hyperledger/fabric-ca:1.5.7
docker.io/hyperledger/fabric-ca:1.5.7
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
[root@hy b43646]# ./install-fabric.sh --fabric-version 2.5.0 binary

Pull Hyperledger Fabric binaries

===> Downloading version 2.5.0 platform specific fabric binaries
===> Downloading:  https://github.com/hyperledger/fabric/releases/download/v2.5.0/hyperledger-fabric-linux-amd64-2.5.0.tar.gz
===> Will unpack to: fabric-samples
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
100 99.3M  100 99.3M    0     0  32.6M      0  0:00:03  0:00:03 --:--:-- 43.0M
==> Done.
===> Downloading version 1.5.7 platform specific fabric-ca-client binary
===> Downloading:  https://github.com/hyperledger/fabric-ca/releases/download/v1.5.7/hyperledger-fabric-ca-linux-amd64-1.5.7.tar.gz
===> Will unpack to: fabric-samples
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
100 34.0M  100 34.0M    0     0  27.4M      0  0:00:01  0:00:01 --:--:-- 42.1M
==> Done.
[root@hy b43646]# ls
fabric-samples  install-fabric.sh
[root@hy b43646]# cd fabric-samples/test-network
[root@hy test-network]# ls
addOrg3     CHAINCODE_AS_A_SERVICE_TUTORIAL.md  configtx          network.config  organizations       README.md  setOrgEnv.sh
bft-config  compose                             monitordocker.sh  network.sh      prometheus-grafana  scripts    system-genesis-block
[root@hy test-network]# ./network.sh up
Using docker and docker-compose
Starting nodes with CLI timeout of '5' tries and CLI delay of '3' seconds and using database 'leveldb' with crypto from 'cryptogen'
LOCAL_VERSION=v2.5.0
DOCKER_IMAGE_VERSION=v2.5.4
Local fabric binaries and docker images are out of  sync. This may cause problems.
/root/go/src/github.com/b43646/fabric-samples/bin/cryptogen
Generating certificates using cryptogen tool
Creating Org1 Identities
+ cryptogen generate --config=./organizations/cryptogen/crypto-config-org1.yaml --output=organizations
org1.example.com
+ res=0
Creating Org2 Identities
+ cryptogen generate --config=./organizations/cryptogen/crypto-config-org2.yaml --output=organizations
org2.example.com
+ res=0
Creating Orderer Org Identities
+ cryptogen generate --config=./organizations/cryptogen/crypto-config-orderer.yaml --output=organizations
+ res=0
Generating CCP files for Org1 and Org2
[+] Running 8/8
 ✔ Network fabric_test                      Created                                                                                                0.3s
 ✔ Volume "compose_orderer.example.com"     Created                                                                                                0.0s
 ✔ Volume "compose_peer0.org1.example.com"  Created                                                                                                0.0s
 ✔ Volume "compose_peer0.org2.example.com"  Created                                                                                                0.0s
 ✔ Container orderer.example.com            Started                                                                                                0.0s
 ✔ Container peer0.org2.example.com         Started                                                                                                0.0s
 ✔ Container peer0.org1.example.com         Started                                                                                                0.0s
 ✔ Container cli                            Started                                                                                                0.0s
CONTAINER ID   IMAGE                               COMMAND             CREATED         STATUS                  PORTS                                                                                                                             NAMES
bf1f99c73f3a   hyperledger/fabric-tools:latest     "/bin/bash"         2 seconds ago   Up Less than a second                                                                                                                                     cli
de35c93780ea   hyperledger/fabric-orderer:latest   "orderer"           2 seconds ago   Up Less than a second   0.0.0.0:7050->7050/tcp, :::7050->7050/tcp, 0.0.0.0:7053->7053/tcp, :::7053->7053/tcp, 0.0.0.0:9443->9443/tcp, :::9443->9443/tcp   orderer.example.com
5e4cbea81eae   hyperledger/fabric-peer:latest      "peer node start"   2 seconds ago   Up Less than a second   0.0.0.0:9051->9051/tcp, :::9051->9051/tcp, 7051/tcp, 0.0.0.0:9445->9445/tcp, :::9445->9445/tcp                                    peer0.org2.example.com
3b68dd30458e   hyperledger/fabric-peer:latest      "peer node start"   2 seconds ago   Up Less than a second   0.0.0.0:7051->7051/tcp, :::7051->7051/tcp, 0.0.0.0:9444->9444/tcp, :::9444->9444/tcp                                              peer0.org1.example.com
[root@hy test-network]# docker ps
CONTAINER ID   IMAGE                               COMMAND             CREATED         STATUS         PORTS                                                                                                                             NAMES
bf1f99c73f3a   hyperledger/fabric-tools:latest     "/bin/bash"         3 minutes ago   Up 3 minutes                                                                                                                                     cli
de35c93780ea   hyperledger/fabric-orderer:latest   "orderer"           3 minutes ago   Up 3 minutes   0.0.0.0:7050->7050/tcp, :::7050->7050/tcp, 0.0.0.0:7053->7053/tcp, :::7053->7053/tcp, 0.0.0.0:9443->9443/tcp, :::9443->9443/tcp   orderer.example.com
5e4cbea81eae   hyperledger/fabric-peer:latest      "peer node start"   3 minutes ago   Up 3 minutes   0.0.0.0:9051->9051/tcp, :::9051->9051/tcp, 7051/tcp, 0.0.0.0:9445->9445/tcp, :::9445->9445/tcp                                    peer0.org2.example.com
3b68dd30458e   hyperledger/fabric-peer:latest      "peer node start"   3 minutes ago   Up 3 minutes   0.0.0.0:7051->7051/tcp, :::7051->7051/tcp, 0.0.0.0:9444->9444/tcp, :::9444->9444/tcp                                              peer0.org1.example.com
[root@hy test-network]# ./network.sh createChannel
Using docker and docker-compose
Creating channel 'mychannel'.
If network is not up, starting nodes with CLI timeout of '5' tries and CLI delay of '3' seconds and using database 'leveldb
Network Running Already
Using docker and docker-compose
Generating channel genesis block 'mychannel.block'
Using organization 1
/root/go/src/github.com/b43646/fabric-samples/bin/configtxgen
+ '[' 0 -eq 1 ']'
+ configtxgen -profile ChannelUsingRaft -outputBlock ./channel-artifacts/mychannel.block -channelID mychannel
2023-10-25 06:43:07.138 GMT 0001 INFO [common.tools.configtxgen] main -> Loading configuration
2023-10-25 06:43:07.143 GMT 0002 INFO [common.tools.configtxgen.localconfig] completeInitialization -> orderer type: etcdraft
2023-10-25 06:43:07.143 GMT 0003 INFO [common.tools.configtxgen.localconfig] completeInitialization -> Orderer.EtcdRaft.Options unset, setting to tick_interval:"500ms" election_tick:10 heartbeat_tick:1 max_inflight_blocks:5 snapshot_interval_size:16777216
2023-10-25 06:43:07.143 GMT 0004 INFO [common.tools.configtxgen.localconfig] Load -> Loaded configuration: /root/go/src/github.com/b43646/fabric-samples/test-network/configtx/configtx.yaml
2023-10-25 06:43:07.145 GMT 0005 INFO [common.tools.configtxgen] doOutputBlock -> Generating genesis block
2023-10-25 06:43:07.145 GMT 0006 INFO [common.tools.configtxgen] doOutputBlock -> Creating application channel genesis block
2023-10-25 06:43:07.146 GMT 0007 INFO [common.tools.configtxgen] doOutputBlock -> Writing genesis block
+ res=0
Creating channel mychannel
Adding orderers
+ . scripts/orderer.sh mychannel
+ '[' 0 -eq 1 ']'
+ res=0
Status: 201
{
        "name": "mychannel",
        "url": "/participation/v1/channels/mychannel",
        "consensusRelation": "consenter",
        "status": "active",
        "height": 1
}

Channel 'mychannel' created
Joining org1 peer to the channel...
Using organization 1
+ peer channel join -b ./channel-artifacts/mychannel.block
+ res=0
2023-10-25 06:43:13.247 GMT 0001 INFO [channelCmd] InitCmdFactory -> Endorser and orderer connections initialized
2023-10-25 06:43:13.269 GMT 0002 INFO [channelCmd] executeJoin -> Successfully submitted proposal to join channel
Joining org2 peer to the channel...
Using organization 2
+ peer channel join -b ./channel-artifacts/mychannel.block
+ res=0
2023-10-25 06:43:16.329 GMT 0001 INFO [channelCmd] InitCmdFactory -> Endorser and orderer connections initialized
2023-10-25 06:43:16.352 GMT 0002 INFO [channelCmd] executeJoin -> Successfully submitted proposal to join channel
Setting anchor peer for org1...
Using organization 1
Fetching channel config for channel mychannel
Using organization 1
Fetching the most recent configuration block for the channel
+ peer channel fetch config config_block.pb -o orderer.example.com:7050 --ordererTLSHostnameOverride orderer.example.com -c mychannel --tls --cafile /opt/gopath/src/github.com/hyperledger/fabric/peer/organizations/ordererOrganizations/example.com/tlsca/tlsca.example.com-cert.pem
2023-10-25 06:43:16.490 UTC 0001 INFO [channelCmd] InitCmdFactory -> Endorser and orderer connections initialized
2023-10-25 06:43:16.492 UTC 0002 INFO [cli.common] readBlock -> Received block: 0
2023-10-25 06:43:16.492 UTC 0003 INFO [channelCmd] fetch -> Retrieving last config block: 0
2023-10-25 06:43:16.493 UTC 0004 INFO [cli.common] readBlock -> Received block: 0
Decoding config block to JSON and isolating config to Org1MSPconfig.json
+ configtxlator proto_decode --input config_block.pb --type common.Block --output config_block.json
+ jq '.data.data[0].payload.data.config' config_block.json
Generating anchor peer update transaction for Org1 on channel mychannel
+ jq '.channel_group.groups.Application.groups.Org1MSP.values += {"AnchorPeers":{"mod_policy": "Admins","value":{"anchor_peers": [{"host": "peer0.org1.example.com","port": 7051}]},"version": "0"}}' Org1MSPconfig.json
+ configtxlator proto_encode --input Org1MSPconfig.json --type common.Config --output original_config.pb
+ configtxlator proto_encode --input Org1MSPmodified_config.json --type common.Config --output modified_config.pb
+ configtxlator compute_update --channel_id mychannel --original original_config.pb --updated modified_config.pb --output config_update.pb
+ configtxlator proto_decode --input config_update.pb --type common.ConfigUpdate --output config_update.json
+ jq .
++ cat config_update.json
+ echo '{"payload":{"header":{"channel_header":{"channel_id":"mychannel", "type":2}},"data":{"config_update":{' '"channel_id":' '"mychannel",' '"isolated_data":' '{},' '"read_set":' '{' '"groups":' '{' '"Application":' '{' '"groups":' '{' '"Org1MSP":' '{' '"groups":' '{},' '"mod_policy":' '"",' '"policies":' '{' '"Admins":' '{' '"mod_policy":' '"",' '"policy":' null, '"version":' '"0"' '},' '"Endorsement":' '{' '"mod_policy":' '"",' '"policy":' null, '"version":' '"0"' '},' '"Readers":' '{' '"mod_policy":' '"",' '"policy":' null, '"version":' '"0"' '},' '"Writers":' '{' '"mod_policy":' '"",' '"policy":' null, '"version":' '"0"' '}' '},' '"values":' '{' '"MSP":' '{' '"mod_policy":' '"",' '"value":' null, '"version":' '"0"' '}' '},' '"version":' '"0"' '}' '},' '"mod_policy":' '"",' '"policies":' '{},' '"values":' '{},' '"version":' '"0"' '}' '},' '"mod_policy":' '"",' '"policies":' '{},' '"values":' '{},' '"version":' '"0"' '},' '"write_set":' '{' '"groups":' '{' '"Application":' '{' '"groups":' '{' '"Org1MSP":' '{' '"groups":' '{},' '"mod_policy":' '"Admins",' '"policies":' '{' '"Admins":' '{' '"mod_policy":' '"",' '"policy":' null, '"version":' '"0"' '},' '"Endorsement":' '{' '"mod_policy":' '"",' '"policy":' null, '"version":' '"0"' '},' '"Readers":' '{' '"mod_policy":' '"",' '"policy":' null, '"version":' '"0"' '},' '"Writers":' '{' '"mod_policy":' '"",' '"policy":' null, '"version":' '"0"' '}' '},' '"values":' '{' '"AnchorPeers":' '{' '"mod_policy":' '"Admins",' '"value":' '{' '"anchor_peers":' '[' '{' '"host":' '"peer0.org1.example.com",' '"port":' 7051 '}' ']' '},' '"version":' '"0"' '},' '"MSP":' '{' '"mod_policy":' '"",' '"value":' null, '"version":' '"0"' '}' '},' '"version":' '"1"' '}' '},' '"mod_policy":' '"",' '"policies":' '{},' '"values":' '{},' '"version":' '"0"' '}' '},' '"mod_policy":' '"",' '"policies":' '{},' '"values":' '{},' '"version":' '"0"' '}' '}}}}'
+ configtxlator proto_encode --input config_update_in_envelope.json --type common.Envelope --output Org1MSPanchors.tx
2023-10-25 06:43:16.766 UTC 0001 INFO [channelCmd] InitCmdFactory -> Endorser and orderer connections initialized
2023-10-25 06:43:16.780 UTC 0002 INFO [channelCmd] update -> Successfully submitted channel update
Anchor peer set for org 'Org1MSP' on channel 'mychannel'
Setting anchor peer for org2...
Using organization 2
Fetching channel config for channel mychannel
Using organization 2
Fetching the most recent configuration block for the channel
+ peer channel fetch config config_block.pb -o orderer.example.com:7050 --ordererTLSHostnameOverride orderer.example.com -c mychannel --tls --cafile /opt/gopath/src/github.com/hyperledger/fabric/peer/organizations/ordererOrganizations/example.com/tlsca/tlsca.example.com-cert.pem
2023-10-25 06:43:16.918 UTC 0001 INFO [channelCmd] InitCmdFactory -> Endorser and orderer connections initialized
2023-10-25 06:43:16.921 UTC 0002 INFO [cli.common] readBlock -> Received block: 1
2023-10-25 06:43:16.921 UTC 0003 INFO [channelCmd] fetch -> Retrieving last config block: 1
2023-10-25 06:43:16.923 UTC 0004 INFO [cli.common] readBlock -> Received block: 1
Decoding config block to JSON and isolating config to Org2MSPconfig.json
+ configtxlator proto_decode --input config_block.pb --type common.Block --output config_block.json
+ jq '.data.data[0].payload.data.config' config_block.json
Generating anchor peer update transaction for Org2 on channel mychannel
+ jq '.channel_group.groups.Application.groups.Org2MSP.values += {"AnchorPeers":{"mod_policy": "Admins","value":{"anchor_peers": [{"host": "peer0.org2.example.com","port": 9051}]},"version": "0"}}' Org2MSPconfig.json
+ configtxlator proto_encode --input Org2MSPconfig.json --type common.Config --output original_config.pb
+ configtxlator proto_encode --input Org2MSPmodified_config.json --type common.Config --output modified_config.pb
+ configtxlator compute_update --channel_id mychannel --original original_config.pb --updated modified_config.pb --output config_update.pb
+ configtxlator proto_decode --input config_update.pb --type common.ConfigUpdate --output config_update.json
+ jq .
++ cat config_update.json
+ echo '{"payload":{"header":{"channel_header":{"channel_id":"mychannel", "type":2}},"data":{"config_update":{' '"channel_id":' '"mychannel",' '"isolated_data":' '{},' '"read_set":' '{' '"groups":' '{' '"Application":' '{' '"groups":' '{' '"Org2MSP":' '{' '"groups":' '{},' '"mod_policy":' '"",' '"policies":' '{' '"Admins":' '{' '"mod_policy":' '"",' '"policy":' null, '"version":' '"0"' '},' '"Endorsement":' '{' '"mod_policy":' '"",' '"policy":' null, '"version":' '"0"' '},' '"Readers":' '{' '"mod_policy":' '"",' '"policy":' null, '"version":' '"0"' '},' '"Writers":' '{' '"mod_policy":' '"",' '"policy":' null, '"version":' '"0"' '}' '},' '"values":' '{' '"MSP":' '{' '"mod_policy":' '"",' '"value":' null, '"version":' '"0"' '}' '},' '"version":' '"0"' '}' '},' '"mod_policy":' '"",' '"policies":' '{},' '"values":' '{},' '"version":' '"0"' '}' '},' '"mod_policy":' '"",' '"policies":' '{},' '"values":' '{},' '"version":' '"0"' '},' '"write_set":' '{' '"groups":' '{' '"Application":' '{' '"groups":' '{' '"Org2MSP":' '{' '"groups":' '{},' '"mod_policy":' '"Admins",' '"policies":' '{' '"Admins":' '{' '"mod_policy":' '"",' '"policy":' null, '"version":' '"0"' '},' '"Endorsement":' '{' '"mod_policy":' '"",' '"policy":' null, '"version":' '"0"' '},' '"Readers":' '{' '"mod_policy":' '"",' '"policy":' null, '"version":' '"0"' '},' '"Writers":' '{' '"mod_policy":' '"",' '"policy":' null, '"version":' '"0"' '}' '},' '"values":' '{' '"AnchorPeers":' '{' '"mod_policy":' '"Admins",' '"value":' '{' '"anchor_peers":' '[' '{' '"host":' '"peer0.org2.example.com",' '"port":' 9051 '}' ']' '},' '"version":' '"0"' '},' '"MSP":' '{' '"mod_policy":' '"",' '"value":' null, '"version":' '"0"' '}' '},' '"version":' '"1"' '}' '},' '"mod_policy":' '"",' '"policies":' '{},' '"values":' '{},' '"version":' '"0"' '}' '},' '"mod_policy":' '"",' '"policies":' '{},' '"values":' '{},' '"version":' '"0"' '}' '}}}}'
+ configtxlator proto_encode --input config_update_in_envelope.json --type common.Envelope --output Org2MSPanchors.tx
2023-10-25 06:43:17.201 UTC 0001 INFO [channelCmd] InitCmdFactory -> Endorser and orderer connections initialized
2023-10-25 06:43:17.216 UTC 0002 INFO [channelCmd] update -> Successfully submitted channel update
Anchor peer set for org 'Org2MSP' on channel 'mychannel'
Channel 'mychannel' joined
[root@hy test-network]# ./network.sh deployCC -ccn basic -ccp ../asset-transfer-basic/chaincode-go -ccl go
Using docker and docker-compose
deploying chaincode on channel 'mychannel'
executing with the following
- CHANNEL_NAME: mychannel
- CC_NAME: basic
- CC_SRC_PATH: ../asset-transfer-basic/chaincode-go
- CC_SRC_LANGUAGE: go
- CC_VERSION: 1.0.1
- CC_SEQUENCE: auto
- CC_END_POLICY: NA
- CC_COLL_CONFIG: NA
- CC_INIT_FCN: NA
- DELAY: 3
- MAX_RETRY: 5
- VERBOSE: false
executing with the following
- CC_NAME: basic
- CC_SRC_PATH: ../asset-transfer-basic/chaincode-go
- CC_SRC_LANGUAGE: go
- CC_VERSION: 1.0.1
Vendoring Go dependencies at ../asset-transfer-basic/chaincode-go
~/go/src/github.com/b43646/fabric-samples/asset-transfer-basic/chaincode-go ~/go/src/github.com/b43646/fabric-samples/test-network
go: downloading github.com/hyperledger/fabric-chaincode-go v0.0.0-20230228194215-b84622ba6a7a
go: downloading github.com/hyperledger/fabric-protos-go v0.3.0
go: downloading google.golang.org/protobuf v1.28.1
go: downloading github.com/hyperledger/fabric-contract-api-go v1.2.1
go: downloading github.com/stretchr/testify v1.8.2
go: downloading github.com/golang/protobuf v1.5.2
go: downloading google.golang.org/grpc v1.53.0
go: downloading golang.org/x/net v0.7.0
go: downloading google.golang.org/genproto v0.0.0-20230110181048-76db0878b65f
go: downloading github.com/xeipuuv/gojsonschema v1.2.0
go: downloading github.com/go-openapi/spec v0.20.8
go: downloading github.com/gobuffalo/packr v1.30.1
go: downloading github.com/davecgh/go-spew v1.1.1
go: downloading github.com/pmezard/go-difflib v1.0.0
go: downloading gopkg.in/yaml.v3 v3.0.1
go: downloading golang.org/x/sys v0.5.0
go: downloading github.com/xeipuuv/gojsonreference v0.0.0-20180127040603-bd5ef7bd5415
go: downloading github.com/go-openapi/jsonpointer v0.19.5
go: downloading github.com/go-openapi/jsonreference v0.20.0
go: downloading github.com/go-openapi/swag v0.21.1
go: downloading github.com/gobuffalo/envy v1.10.1
go: downloading github.com/gobuffalo/packd v1.0.1
go: downloading github.com/xeipuuv/gojsonpointer v0.0.0-20190905194746-02993c407bfb
go: downloading github.com/mailru/easyjson v0.7.7
go: downloading gopkg.in/yaml.v2 v2.4.0
go: downloading github.com/joho/godotenv v1.4.0
go: downloading github.com/rogpeppe/go-internal v1.8.1
go: downloading golang.org/x/text v0.7.0
go: downloading github.com/josharian/intern v1.0.0
~/go/src/github.com/b43646/fabric-samples/test-network
Finished vendoring Go dependencies
+ '[' false = true ']'
+ peer lifecycle chaincode package basic.tar.gz --path ../asset-transfer-basic/chaincode-go --lang golang --label basic_1.0.1
+ res=0
Chaincode is packaged
Installing chaincode on peer0.org1...
Using organization 1
+ peer lifecycle chaincode queryinstalled --output json
+ jq -r 'try (.installed_chaincodes[].package_id)'
+ grep '^basic_1.0.1:650b7b4f5a8545d710651dc01edee8cf83518ef4b36a67a08be061ba14da653a$'
+ test 1 -ne 0
+ peer lifecycle chaincode install basic.tar.gz
+ res=0
2023-10-25 06:51:11.157 GMT 0001 INFO [cli.lifecycle.chaincode] submitInstallProposal -> Installed remotely: response:<status:200 payload:"\nLbasic_1.0.1:650b7b4f5a8545d710651dc01edee8cf83518ef4b36a67a08be061ba14da653a\022\013basic_1.0.1" >
2023-10-25 06:51:11.158 GMT 0002 INFO [cli.lifecycle.chaincode] submitInstallProposal -> Chaincode code package identifier: basic_1.0.1:650b7b4f5a8545d710651dc01edee8cf83518ef4b36a67a08be061ba14da653a
Chaincode is installed on peer0.org1
Install chaincode on peer0.org2...
Using organization 2
+ peer lifecycle chaincode queryinstalled --output json
+ jq -r 'try (.installed_chaincodes[].package_id)'
+ grep '^basic_1.0.1:650b7b4f5a8545d710651dc01edee8cf83518ef4b36a67a08be061ba14da653a$'
+ test 1 -ne 0
+ peer lifecycle chaincode install basic.tar.gz
+ res=0
2023-10-25 06:51:37.162 GMT 0001 INFO [cli.lifecycle.chaincode] submitInstallProposal -> Installed remotely: response:<status:200 payload:"\nLbasic_1.0.1:650b7b4f5a8545d710651dc01edee8cf83518ef4b36a67a08be061ba14da653a\022\013basic_1.0.1" >
2023-10-25 06:51:37.162 GMT 0002 INFO [cli.lifecycle.chaincode] submitInstallProposal -> Chaincode code package identifier: basic_1.0.1:650b7b4f5a8545d710651dc01edee8cf83518ef4b36a67a08be061ba14da653a
Chaincode is installed on peer0.org2
++ peer lifecycle chaincode querycommitted --channelID mychannel --name basic
++ sed -n '/Version:/{s/.*Sequence: //; s/, Endorsement Plugin:.*$//; p;}'
Error: query failed with status: 404 - namespace basic is not defined
+ COMMITTED_CC_SEQUENCE=
+ res=0
Using organization 1
+ peer lifecycle chaincode queryinstalled --output json
+ jq -r 'try (.installed_chaincodes[].package_id)'
+ grep '^basic_1.0.1:650b7b4f5a8545d710651dc01edee8cf83518ef4b36a67a08be061ba14da653a$'
+ res=0
basic_1.0.1:650b7b4f5a8545d710651dc01edee8cf83518ef4b36a67a08be061ba14da653a
Query installed successful on peer0.org1 on channel
Using organization 1
+ peer lifecycle chaincode approveformyorg -o localhost:7050 --ordererTLSHostnameOverride orderer.example.com --tls --cafile /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/ordererOrganizations/example.com/tlsca/tlsca.example.com-cert.pem --channelID mychannel --name basic --version 1.0.1 --package-id basic_1.0.1:650b7b4f5a8545d710651dc01edee8cf83518ef4b36a67a08be061ba14da653a --sequence 1
+ res=0
2023-10-25 06:51:39.369 GMT 0001 INFO [chaincodeCmd] ClientWait -> txid [f043e21e06bcee95aac0212a55e3cfe6bdc8b0b4672b8a8fc19bb929ced62515] committed with status (VALID) at localhost:7051
Chaincode definition approved on peer0.org1 on channel 'mychannel'
Using organization 1
Checking the commit readiness of the chaincode definition on peer0.org1 on channel 'mychannel'...
Attempting to check the commit readiness of the chaincode definition on peer0.org1, Retry after 3 seconds.
+ peer lifecycle chaincode checkcommitreadiness --channelID mychannel --name basic --version 1.0.1 --sequence 1 --output json
+ res=0
{
        "approvals": {
                "Org1MSP": true,
                "Org2MSP": false
        }
}
Checking the commit readiness of the chaincode definition successful on peer0.org1 on channel 'mychannel'
Using organization 2
Checking the commit readiness of the chaincode definition on peer0.org2 on channel 'mychannel'...
Attempting to check the commit readiness of the chaincode definition on peer0.org2, Retry after 3 seconds.
+ peer lifecycle chaincode checkcommitreadiness --channelID mychannel --name basic --version 1.0.1 --sequence 1 --output json
+ res=0
{
        "approvals": {
                "Org1MSP": true,
                "Org2MSP": false
        }
}
Checking the commit readiness of the chaincode definition successful on peer0.org2 on channel 'mychannel'
Using organization 2
+ peer lifecycle chaincode approveformyorg -o localhost:7050 --ordererTLSHostnameOverride orderer.example.com --tls --cafile /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/ordererOrganizations/example.com/tlsca/tlsca.example.com-cert.pem --channelID mychannel --name basic --version 1.0.1 --package-id basic_1.0.1:650b7b4f5a8545d710651dc01edee8cf83518ef4b36a67a08be061ba14da653a --sequence 1
+ res=0
2023-10-25 06:51:47.584 GMT 0001 INFO [chaincodeCmd] ClientWait -> txid [a287ab6b049c21d0368177a0e9f8e3da19dfc5a584c1c4506108d7f2c06176a3] committed with status (VALID) at localhost:9051
Chaincode definition approved on peer0.org2 on channel 'mychannel'
Using organization 1
Checking the commit readiness of the chaincode definition on peer0.org1 on channel 'mychannel'...
Attempting to check the commit readiness of the chaincode definition on peer0.org1, Retry after 3 seconds.
+ peer lifecycle chaincode checkcommitreadiness --channelID mychannel --name basic --version 1.0.1 --sequence 1 --output json
+ res=0
{
        "approvals": {
                "Org1MSP": true,
                "Org2MSP": true
        }
}
Checking the commit readiness of the chaincode definition successful on peer0.org1 on channel 'mychannel'
Using organization 2
Checking the commit readiness of the chaincode definition on peer0.org2 on channel 'mychannel'...
Attempting to check the commit readiness of the chaincode definition on peer0.org2, Retry after 3 seconds.
+ peer lifecycle chaincode checkcommitreadiness --channelID mychannel --name basic --version 1.0.1 --sequence 1 --output json
+ res=0
{
        "approvals": {
                "Org1MSP": true,
                "Org2MSP": true
        }
}
Checking the commit readiness of the chaincode definition successful on peer0.org2 on channel 'mychannel'
Using organization 1
Using organization 2
+ peer lifecycle chaincode commit -o localhost:7050 --ordererTLSHostnameOverride orderer.example.com --tls --cafile /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/ordererOrganizations/example.com/tlsca/tlsca.example.com-cert.pem --channelID mychannel --name basic --peerAddresses localhost:7051 --tlsRootCertFiles /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/tlsca/tlsca.org1.example.com-cert.pem --peerAddresses localhost:9051 --tlsRootCertFiles /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/tlsca/tlsca.org2.example.com-cert.pem --version 1.0.1 --sequence 1
+ res=0
2023-10-25 06:51:55.927 GMT 0001 INFO [chaincodeCmd] ClientWait -> txid [75136d2f6feb4b5e3f3145aa5cc7509ba0e791dd7bc4dffcfc4b0472b5a78ecf] committed with status (VALID) at localhost:9051
2023-10-25 06:51:55.939 GMT 0002 INFO [chaincodeCmd] ClientWait -> txid [75136d2f6feb4b5e3f3145aa5cc7509ba0e791dd7bc4dffcfc4b0472b5a78ecf] committed with status (VALID) at localhost:7051
Chaincode definition committed on channel 'mychannel'
Using organization 1
Querying chaincode definition on peer0.org1 on channel 'mychannel'...
Attempting to Query committed status on peer0.org1, Retry after 3 seconds.
+ peer lifecycle chaincode querycommitted --channelID mychannel --name basic
+ res=0
Committed chaincode definition for chaincode 'basic' on channel 'mychannel':
Version: 1.0.1, Sequence: 1, Endorsement Plugin: escc, Validation Plugin: vscc, Approvals: [Org1MSP: true, Org2MSP: true]
Query chaincode definition successful on peer0.org1 on channel 'mychannel'
Using organization 2
Querying chaincode definition on peer0.org2 on channel 'mychannel'...
Attempting to Query committed status on peer0.org2, Retry after 3 seconds.
+ peer lifecycle chaincode querycommitted --channelID mychannel --name basic
+ res=0
Committed chaincode definition for chaincode 'basic' on channel 'mychannel':
Version: 1.0.1, Sequence: 1, Endorsement Plugin: escc, Validation Plugin: vscc, Approvals: [Org1MSP: true, Org2MSP: true]
Query chaincode definition successful on peer0.org2 on channel 'mychannel'
Chaincode initialization is not required
[root@hy test-network]# ls
addOrg3       CHAINCODE_AS_A_SERVICE_TUTORIAL.md  configtx          network.config  prometheus-grafana  setOrgEnv.sh
basic.tar.gz  channel-artifacts                   log.txt           network.sh      README.md           system-genesis-block
bft-config    compose                             monitordocker.sh  organizations   scripts
[root@hy test-network]# ls ../
asset-transfer-abac               auction-dutch       CODEOWNERS                       MAINTAINERS.md    test-network-nano-bash
asset-transfer-basic              auction-simple      config                           off_chain_data    token-erc-1155
asset-transfer-events             bin                 CONTRIBUTING.md                  README.md         token-erc-20
asset-transfer-ledger-queries     builders            full-stack-asset-transfer-guide  SECURITY.md       token-erc-721
asset-transfer-private-data       CHANGELOG.md        hardware-security-module         test-application  token-sdk
asset-transfer-sbe                ci                  high-throughput                  test-network      token-utxo
asset-transfer-secured-agreement  CODE_OF_CONDUCT.md  LICENSE                          test-network-k8s
[root@hy test-network]# ls ../bin
configtxgen  configtxlator  cryptogen  discover  fabric-ca-client  fabric-ca-server  ledgerutil  orderer  osnadmin  peer
[root@hy test-network]# pwd
/root/go/src/github.com/b43646/fabric-samples/test-network
[root@hy test-network]# export PATH=${PWD}/../bin:$PATH
[root@hy test-network]# export CORE_PEER_TLS_ENABLED=true
[root@hy test-network]# export CORE_PEER_LOCALMSPID="Org1MSP"
[root@hy test-network]# export CORE_PEER_TLS_ROOTCERT_FILE=${PWD}/organizations/peerOrganizations/org1.example.com/peers/peer0.org1.example.com/tls/ca.crt
[root@hy test-network]# export CORE_PEER_MSPCONFIGPATH=${PWD}/organizations/peerOrganizations/org1.example.com/users/Admin@org1.example.com/msp
[root@hy test-network]# export CORE_PEER_ADDRESS=localhost:7051
[root@hy test-network]#
[root@hy test-network]#
[root@hy test-network]#
[root@hy test-network]# peer chaincode invoke -o localhost:7050 --ordererTLSHostnameOverride orderer.example.com --tls --cafile "${PWD}/organizations/ordererOrganizations/example.com/orderers/orderer.example.com/msp/tlscacerts/tlsca.example.com-cert.pem" -C mychannel -n basic --peerAddresses localhost:7051 --tlsRootCertFiles "${PWD}/organizations/peerOrganizations/org1.example.com/peers/peer0.org1.example.com/tls/ca.crt" --peerAddresses localhost:9051 --tlsRootCertFiles "${PWD}/organizations/peerOrganizations/org2.example.com/peers/peer0.org2.example.com/tls/ca.crt" -c '{"function":"InitLedger","Args":[]}'
2023-10-25 06:57:15.700 GMT 0001 ERRO [main] InitCmd -> Fatal error when initializing core config : error when reading core config file: Config File "core" Not Found in "[/root/go/src/github.com/b43646/fabric-samples/test-network]"
[root@hy test-network]# export FABRIC_CFG_PATH=$PWD/../config/
[root@hy test-network]# ls ../config/
configtx.yaml  core.yaml  orderer.yaml
[root@hy test-network]# peer chaincode invoke -o localhost:7050 --ordererTLSHostnameOverride orderer.example.com --tls --cafile "${PWD}/organizations/ordererOrganizations/example.com/orderers/orderer.example.com/msp/tlscacerts/tlsca.example.com-cert.pem" -C mychannel -n basic --peerAddresses localhost:7051 --tlsRootCertFiles "${PWD}/organizations/peerOrganizations/org1.example.com/peers/peer0.org1.example.com/tls/ca.crt" --peerAddresses localhost:9051 --tlsRootCertFiles "${PWD}/organizations/peerOrganizations/org2.example.com/peers/peer0.org2.example.com/tls/ca.crt" -c '{"function":"InitLedger","Args":[]}'
2023-10-25 06:58:24.346 GMT 0001 INFO [chaincodeCmd] chaincodeInvokeOrQuery -> Chaincode invoke successful. result: status:200
[root@hy test-network]# peer chaincode query -C mychannel -n basic -c '{"Args":["GetAllAssets"]}'
[{"AppraisedValue":300,"Color":"blue","ID":"asset1","Owner":"Tomoko","Size":5},{"AppraisedValue":400,"Color":"red","ID":"asset2","Owner":"Brad","Size":5},{"AppraisedValue":500,"Color":"green","ID":"asset3","Owner":"Jin Soo","Size":10},{"AppraisedValue":600,"Color":"yellow","ID":"asset4","Owner":"Max","Size":10},{"AppraisedValue":700,"Color":"black","ID":"asset5","Owner":"Adriana","Size":15},{"AppraisedValue":800,"Color":"white","ID":"asset6","Owner":"Michel","Size":15}]
[root@hy test-network]#
[root@hy test-network]#
[root@hy test-network]#
[root@hy test-network]# peer chaincode invoke -o localhost:7050 --ordererTLSHostnameOverride orderer.example.com --tls --cafile "${PWD}/organizations/ordererOrganizations/example.com/orderers/orderer.example.com/msp/tlscacerts/tlsca.example.com-cert.pem" -C mychannel -n basic --peerAddresses localhost:7051 --tlsRootCertFiles "${PWD}/organizations/peerOrganizations/org1.example.com/peers/peer0.org1.example.com/tls/ca.crt" --peerAddresses localhost:9051 --tlsRootCertFiles "${PWD}/organizations/peerOrganizations/org2.example.com/peers/peer0.org2.example.com/tls/ca.crt" -c '{"function":"TransferAsset","Args":["asset6","Christopher"]}'
2023-10-25 07:01:32.806 GMT 0001 INFO [chaincodeCmd] chaincodeInvokeOrQuery -> Chaincode invoke successful. result: status:200 payload:"Michel"
[root@hy test-network]#
[root@hy test-network]#
[root@hy test-network]#
[root@hy test-network]# export CORE_PEER_TLS_ENABLED=true
[root@hy test-network]# export CORE_PEER_LOCALMSPID="Org2MSP"
[root@hy test-network]# export CORE_PEER_TLS_ROOTCERT_FILE=${PWD}/organizations/peerOrganizations/org2.example.com/peers/peer0.org2.example.com/tls/ca.crt
[root@hy test-network]# export CORE_PEER_MSPCONFIGPATH=${PWD}/organizations/peerOrganizations/org2.example.com/users/Admin@org2.example.com/msp
[root@hy test-network]# export CORE_PEER_ADDRESS=localhost:9051
[root@hy test-network]#
[root@hy test-network]# peer chaincode query -C mychannel -n basic -c '{"Args":["ReadAsset","asset6"]}'
{"AppraisedValue":800,"Color":"white","ID":"asset6","Owner":"Christopher","Size":15}

[root@hy test-network]# ./network.sh down
Using docker and docker-compose
Stopping network
[+] Running 12/12
 ✔ Container cli                          Removed                                                                                                  0.5s
 ✔ Container orderer.example.com          Removed                                                                                                  1.5s
 ✔ Container peer0.org2.example.com       Removed                                                                                                  2.0s
 ✔ Container peer0.org1.example.com       Removed                                                                                                  2.2s
 ✔ Volume compose_orderer2.example.com    Removed                                                                                                  0.0s
 ✔ Volume compose_peer0.org1.example.com  Removed                                                                                                  0.0s
 ✔ Volume compose_peer0.org2.example.com  Removed                                                                                                  0.0s
 ✔ Volume compose_orderer3.example.com    Removed                                                                                                  0.0s
 ✔ Volume compose_orderer4.example.com    Removed                                                                                                  0.0s
 ✔ Volume compose_peer0.org3.example.com  Removed                                                                                                  0.0s
 ✔ Volume compose_orderer.example.com     Removed                                                                                                  0.0s
 ✔ Network fabric_test                    Removed                                                                                                  0.2s
Error response from daemon: get docker_orderer.example.com: no such volume
Error response from daemon: get docker_peer0.org1.example.com: no such volume
Error response from daemon: get docker_peer0.org2.example.com: no such volume
Removing remaining containers
Removing generated chaincode docker images
Untagged: dev-peer0.org2.example.com-basic_1.0.1-650b7b4f5a8545d710651dc01edee8cf83518ef4b36a67a08be061ba14da653a-c0a713c435d5298d7e406d76938453c6295ec064a3b830682335e59970b8be78:latest
Deleted: sha256:6399d87d9368f4c614df3a9dede32a8e5ea454eecea71c33f598d12dcdbb140b
Deleted: sha256:d8165b1a820bdfcb475b72af31800963b5f80ea97998b8763f57e71a64b01523
Deleted: sha256:16bf7ae525fa415d84147a74bed0a148d522d83b1fb17c55a01ba221cb0155e8
Deleted: sha256:98a70daf137313550dc6cdb059badb0ea9aa2a5f81da820470b2698f42c2c1a5
Untagged: dev-peer0.org1.example.com-basic_1.0.1-650b7b4f5a8545d710651dc01edee8cf83518ef4b36a67a08be061ba14da653a-20086c6927e952735a27a90ceb7546bf364568aa2d1f2d3b0a8fde53dfe8f69d:latest
Deleted: sha256:af38d6efecb9fabd7a4eab73c378a8e5a9894138fcc4f6a6142e47b1a18ba812
Deleted: sha256:67626003247d937a24751d1c376cc685cf4b715f0e2a632a842f064edf48c5ad
Deleted: sha256:35541f630fff3928c4a60854c39d51cc00713349dd104b5728949ba5712bbb93
Deleted: sha256:82f29bd8c89781e32747f9bfe934ea4459ededbd245f6a03ab2cf2f5928ed401
Unable to find image 'busybox:latest' locally
latest: Pulling from library/busybox
3f4d90098f5b: Pull complete
Digest: sha256:3fbc632167424a6d997e74f52b878d7cc478225cffac6bc977eedfe51c7f4e79
Status: Downloaded newer image for busybox:latest

```
