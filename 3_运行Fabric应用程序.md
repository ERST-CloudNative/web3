

```
[root@hy test-network]# ./network.sh up createChannel -c mychannel -ca
Using docker and docker-compose
Creating channel 'mychannel'.
If network is not up, starting nodes with CLI timeout of '5' tries and CLI delay of '3' seconds and using database 'leveldb with crypto from 'Certificate Authorities'
Bringing up network
LOCAL_VERSION=v2.5.0
DOCKER_IMAGE_VERSION=v2.5.4
Local fabric binaries and docker images are out of  sync. This may cause problems.
CA_LOCAL_VERSION=v1.5.7
CA_DOCKER_IMAGE_VERSION=v1.5.7
Generating certificates using Fabric CA
[+] Running 4/4
 ✔ Network fabric_test   Created                                                                                                                   0.3s
 ✔ Container ca_org2     Started                                                                                                                   0.0s
 ✔ Container ca_orderer  Started                                                                                                                   0.0s
 ✔ Container ca_org1     Started                                                                                                                   0.0s
Creating Org1 Identities
Enrolling the CA admin
+ fabric-ca-client enroll -u https://admin:adminpw@localhost:7054 --caname ca-org1 --tls.certfiles /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/fabric-ca/org1/ca-cert.pem
2023/10/25 08:41:59 [INFO] Created a default configuration file at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/fabric-ca-client-config.yaml
2023/10/25 08:41:59 [INFO] TLS Enabled
2023/10/25 08:41:59 [INFO] generating key: &{A:ecdsa S:256}
2023/10/25 08:41:59 [INFO] encoded CSR
2023/10/25 08:41:59 [INFO] Stored client certificate at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/msp/signcerts/cert.pem
2023/10/25 08:41:59 [INFO] Stored root CA certificate at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/msp/cacerts/localhost-7054-ca-org1.pem
2023/10/25 08:41:59 [INFO] Stored Issuer public key at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/msp/IssuerPublicKey
2023/10/25 08:41:59 [INFO] Stored Issuer revocation public key at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/msp/IssuerRevocationPublicKey
Registering peer0
+ fabric-ca-client register --caname ca-org1 --id.name peer0 --id.secret peer0pw --id.type peer --tls.certfiles /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/fabric-ca/org1/ca-cert.pem
2023/10/25 08:41:59 [INFO] Configuration file location: /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/fabric-ca-client-config.yaml
2023/10/25 08:41:59 [INFO] TLS Enabled
2023/10/25 08:41:59 [INFO] TLS Enabled
Password: peer0pw
Registering user
+ fabric-ca-client register --caname ca-org1 --id.name user1 --id.secret user1pw --id.type client --tls.certfiles /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/fabric-ca/org1/ca-cert.pem
2023/10/25 08:41:59 [INFO] Configuration file location: /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/fabric-ca-client-config.yaml
2023/10/25 08:41:59 [INFO] TLS Enabled
2023/10/25 08:41:59 [INFO] TLS Enabled
Password: user1pw
Registering the org admin
+ fabric-ca-client register --caname ca-org1 --id.name org1admin --id.secret org1adminpw --id.type admin --tls.certfiles /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/fabric-ca/org1/ca-cert.pem
2023/10/25 08:41:59 [INFO] Configuration file location: /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/fabric-ca-client-config.yaml
2023/10/25 08:41:59 [INFO] TLS Enabled
2023/10/25 08:41:59 [INFO] TLS Enabled
Password: org1adminpw
Generating the peer0 msp
+ fabric-ca-client enroll -u https://peer0:peer0pw@localhost:7054 --caname ca-org1 -M /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/peers/peer0.org1.example.com/msp --tls.certfiles /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/fabric-ca/org1/ca-cert.pem
2023/10/25 08:41:59 [INFO] TLS Enabled
2023/10/25 08:41:59 [INFO] generating key: &{A:ecdsa S:256}
2023/10/25 08:41:59 [INFO] encoded CSR
2023/10/25 08:41:59 [INFO] Stored client certificate at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/peers/peer0.org1.example.com/msp/signcerts/cert.pem
2023/10/25 08:41:59 [INFO] Stored root CA certificate at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/peers/peer0.org1.example.com/msp/cacerts/localhost-7054-ca-org1.pem
2023/10/25 08:41:59 [INFO] Stored Issuer public key at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/peers/peer0.org1.example.com/msp/IssuerPublicKey
2023/10/25 08:41:59 [INFO] Stored Issuer revocation public key at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/peers/peer0.org1.example.com/msp/IssuerRevocationPublicKey
Generating the peer0-tls certificates, use --csr.hosts to specify Subject Alternative Names
+ fabric-ca-client enroll -u https://peer0:peer0pw@localhost:7054 --caname ca-org1 -M /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/peers/peer0.org1.example.com/tls --enrollment.profile tls --csr.hosts peer0.org1.example.com --csr.hosts localhost --tls.certfiles /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/fabric-ca/org1/ca-cert.pem
2023/10/25 08:41:59 [INFO] TLS Enabled
2023/10/25 08:41:59 [INFO] generating key: &{A:ecdsa S:256}
2023/10/25 08:41:59 [INFO] encoded CSR
2023/10/25 08:41:59 [INFO] Stored client certificate at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/peers/peer0.org1.example.com/tls/signcerts/cert.pem
2023/10/25 08:41:59 [INFO] Stored TLS root CA certificate at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/peers/peer0.org1.example.com/tls/tlscacerts/tls-localhost-7054-ca-org1.pem
2023/10/25 08:41:59 [INFO] Stored Issuer public key at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/peers/peer0.org1.example.com/tls/IssuerPublicKey
2023/10/25 08:41:59 [INFO] Stored Issuer revocation public key at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/peers/peer0.org1.example.com/tls/IssuerRevocationPublicKey
Generating the user msp
+ fabric-ca-client enroll -u https://user1:user1pw@localhost:7054 --caname ca-org1 -M /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/users/User1@org1.example.com/msp --tls.certfiles /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/fabric-ca/org1/ca-cert.pem
2023/10/25 08:42:00 [INFO] TLS Enabled
2023/10/25 08:42:00 [INFO] generating key: &{A:ecdsa S:256}
2023/10/25 08:42:00 [INFO] encoded CSR
2023/10/25 08:42:00 [INFO] Stored client certificate at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/users/User1@org1.example.com/msp/signcerts/cert.pem
2023/10/25 08:42:00 [INFO] Stored root CA certificate at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/users/User1@org1.example.com/msp/cacerts/localhost-7054-ca-org1.pem
2023/10/25 08:42:00 [INFO] Stored Issuer public key at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/users/User1@org1.example.com/msp/IssuerPublicKey
2023/10/25 08:42:00 [INFO] Stored Issuer revocation public key at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/users/User1@org1.example.com/msp/IssuerRevocationPublicKey
Generating the org admin msp
+ fabric-ca-client enroll -u https://org1admin:org1adminpw@localhost:7054 --caname ca-org1 -M /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/users/Admin@org1.example.com/msp --tls.certfiles /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/fabric-ca/org1/ca-cert.pem
2023/10/25 08:42:00 [INFO] TLS Enabled
2023/10/25 08:42:00 [INFO] generating key: &{A:ecdsa S:256}
2023/10/25 08:42:00 [INFO] encoded CSR
2023/10/25 08:42:00 [INFO] Stored client certificate at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/users/Admin@org1.example.com/msp/signcerts/cert.pem
2023/10/25 08:42:00 [INFO] Stored root CA certificate at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/users/Admin@org1.example.com/msp/cacerts/localhost-7054-ca-org1.pem
2023/10/25 08:42:00 [INFO] Stored Issuer public key at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/users/Admin@org1.example.com/msp/IssuerPublicKey
2023/10/25 08:42:00 [INFO] Stored Issuer revocation public key at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org1.example.com/users/Admin@org1.example.com/msp/IssuerRevocationPublicKey
Creating Org2 Identities
Enrolling the CA admin
+ fabric-ca-client enroll -u https://admin:adminpw@localhost:8054 --caname ca-org2 --tls.certfiles /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/fabric-ca/org2/ca-cert.pem
2023/10/25 08:42:00 [INFO] Created a default configuration file at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/fabric-ca-client-config.yaml
2023/10/25 08:42:00 [INFO] TLS Enabled
2023/10/25 08:42:00 [INFO] generating key: &{A:ecdsa S:256}
2023/10/25 08:42:00 [INFO] encoded CSR
2023/10/25 08:42:00 [INFO] Stored client certificate at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/msp/signcerts/cert.pem
2023/10/25 08:42:00 [INFO] Stored root CA certificate at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/msp/cacerts/localhost-8054-ca-org2.pem
2023/10/25 08:42:00 [INFO] Stored Issuer public key at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/msp/IssuerPublicKey
2023/10/25 08:42:00 [INFO] Stored Issuer revocation public key at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/msp/IssuerRevocationPublicKey
Registering peer0
+ fabric-ca-client register --caname ca-org2 --id.name peer0 --id.secret peer0pw --id.type peer --tls.certfiles /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/fabric-ca/org2/ca-cert.pem
2023/10/25 08:42:00 [INFO] Configuration file location: /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/fabric-ca-client-config.yaml
2023/10/25 08:42:00 [INFO] TLS Enabled
2023/10/25 08:42:00 [INFO] TLS Enabled
Password: peer0pw
Registering user
+ fabric-ca-client register --caname ca-org2 --id.name user1 --id.secret user1pw --id.type client --tls.certfiles /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/fabric-ca/org2/ca-cert.pem
2023/10/25 08:42:00 [INFO] Configuration file location: /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/fabric-ca-client-config.yaml
2023/10/25 08:42:00 [INFO] TLS Enabled
2023/10/25 08:42:00 [INFO] TLS Enabled
Password: user1pw
Registering the org admin
+ fabric-ca-client register --caname ca-org2 --id.name org2admin --id.secret org2adminpw --id.type admin --tls.certfiles /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/fabric-ca/org2/ca-cert.pem
2023/10/25 08:42:00 [INFO] Configuration file location: /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/fabric-ca-client-config.yaml
2023/10/25 08:42:00 [INFO] TLS Enabled
2023/10/25 08:42:00 [INFO] TLS Enabled
Password: org2adminpw
Generating the peer0 msp
+ fabric-ca-client enroll -u https://peer0:peer0pw@localhost:8054 --caname ca-org2 -M /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/peers/peer0.org2.example.com/msp --tls.certfiles /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/fabric-ca/org2/ca-cert.pem
2023/10/25 08:42:01 [INFO] TLS Enabled
2023/10/25 08:42:01 [INFO] generating key: &{A:ecdsa S:256}
2023/10/25 08:42:01 [INFO] encoded CSR
2023/10/25 08:42:01 [INFO] Stored client certificate at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/peers/peer0.org2.example.com/msp/signcerts/cert.pem
2023/10/25 08:42:01 [INFO] Stored root CA certificate at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/peers/peer0.org2.example.com/msp/cacerts/localhost-8054-ca-org2.pem
2023/10/25 08:42:01 [INFO] Stored Issuer public key at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/peers/peer0.org2.example.com/msp/IssuerPublicKey
2023/10/25 08:42:01 [INFO] Stored Issuer revocation public key at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/peers/peer0.org2.example.com/msp/IssuerRevocationPublicKey
Generating the peer0-tls certificates, use --csr.hosts to specify Subject Alternative Names
+ fabric-ca-client enroll -u https://peer0:peer0pw@localhost:8054 --caname ca-org2 -M /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/peers/peer0.org2.example.com/tls --enrollment.profile tls --csr.hosts peer0.org2.example.com --csr.hosts localhost --tls.certfiles /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/fabric-ca/org2/ca-cert.pem
2023/10/25 08:42:01 [INFO] TLS Enabled
2023/10/25 08:42:01 [INFO] generating key: &{A:ecdsa S:256}
2023/10/25 08:42:01 [INFO] encoded CSR
2023/10/25 08:42:01 [INFO] Stored client certificate at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/peers/peer0.org2.example.com/tls/signcerts/cert.pem
2023/10/25 08:42:01 [INFO] Stored TLS root CA certificate at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/peers/peer0.org2.example.com/tls/tlscacerts/tls-localhost-8054-ca-org2.pem
2023/10/25 08:42:01 [INFO] Stored Issuer public key at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/peers/peer0.org2.example.com/tls/IssuerPublicKey
2023/10/25 08:42:01 [INFO] Stored Issuer revocation public key at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/peers/peer0.org2.example.com/tls/IssuerRevocationPublicKey
Generating the user msp
+ fabric-ca-client enroll -u https://user1:user1pw@localhost:8054 --caname ca-org2 -M /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/users/User1@org2.example.com/msp --tls.certfiles /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/fabric-ca/org2/ca-cert.pem
2023/10/25 08:42:01 [INFO] TLS Enabled
2023/10/25 08:42:01 [INFO] generating key: &{A:ecdsa S:256}
2023/10/25 08:42:01 [INFO] encoded CSR
2023/10/25 08:42:01 [INFO] Stored client certificate at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/users/User1@org2.example.com/msp/signcerts/cert.pem
2023/10/25 08:42:01 [INFO] Stored root CA certificate at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/users/User1@org2.example.com/msp/cacerts/localhost-8054-ca-org2.pem
2023/10/25 08:42:01 [INFO] Stored Issuer public key at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/users/User1@org2.example.com/msp/IssuerPublicKey
2023/10/25 08:42:01 [INFO] Stored Issuer revocation public key at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/users/User1@org2.example.com/msp/IssuerRevocationPublicKey
Generating the org admin msp
+ fabric-ca-client enroll -u https://org2admin:org2adminpw@localhost:8054 --caname ca-org2 -M /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/users/Admin@org2.example.com/msp --tls.certfiles /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/fabric-ca/org2/ca-cert.pem
2023/10/25 08:42:01 [INFO] TLS Enabled
2023/10/25 08:42:01 [INFO] generating key: &{A:ecdsa S:256}
2023/10/25 08:42:01 [INFO] encoded CSR
2023/10/25 08:42:01 [INFO] Stored client certificate at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/users/Admin@org2.example.com/msp/signcerts/cert.pem
2023/10/25 08:42:01 [INFO] Stored root CA certificate at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/users/Admin@org2.example.com/msp/cacerts/localhost-8054-ca-org2.pem
2023/10/25 08:42:01 [INFO] Stored Issuer public key at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/users/Admin@org2.example.com/msp/IssuerPublicKey
2023/10/25 08:42:01 [INFO] Stored Issuer revocation public key at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/peerOrganizations/org2.example.com/users/Admin@org2.example.com/msp/IssuerRevocationPublicKey
Creating Orderer Org Identities
Enrolling the CA admin
+ fabric-ca-client enroll -u https://admin:adminpw@localhost:9054 --caname ca-orderer --tls.certfiles /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/fabric-ca/ordererOrg/ca-cert.pem
2023/10/25 08:42:01 [INFO] Created a default configuration file at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/ordererOrganizations/example.com/fabric-ca-client-config.yaml
2023/10/25 08:42:01 [INFO] TLS Enabled
2023/10/25 08:42:01 [INFO] generating key: &{A:ecdsa S:256}
2023/10/25 08:42:01 [INFO] encoded CSR
2023/10/25 08:42:01 [INFO] Stored client certificate at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/ordererOrganizations/example.com/msp/signcerts/cert.pem
2023/10/25 08:42:01 [INFO] Stored root CA certificate at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/ordererOrganizations/example.com/msp/cacerts/localhost-9054-ca-orderer.pem
2023/10/25 08:42:01 [INFO] Stored Issuer public key at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/ordererOrganizations/example.com/msp/IssuerPublicKey
2023/10/25 08:42:01 [INFO] Stored Issuer revocation public key at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/ordererOrganizations/example.com/msp/IssuerRevocationPublicKey
Registering orderer
+ fabric-ca-client register --caname ca-orderer --id.name orderer --id.secret ordererpw --id.type orderer --tls.certfiles /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/fabric-ca/ordererOrg/ca-cert.pem
2023/10/25 08:42:01 [INFO] Configuration file location: /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/ordererOrganizations/example.com/fabric-ca-client-config.yaml
2023/10/25 08:42:01 [INFO] TLS Enabled
2023/10/25 08:42:01 [INFO] TLS Enabled
Password: ordererpw
Registering the orderer admin
+ fabric-ca-client register --caname ca-orderer --id.name ordererAdmin --id.secret ordererAdminpw --id.type admin --tls.certfiles /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/fabric-ca/ordererOrg/ca-cert.pem
2023/10/25 08:42:02 [INFO] Configuration file location: /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/ordererOrganizations/example.com/fabric-ca-client-config.yaml
2023/10/25 08:42:02 [INFO] TLS Enabled
2023/10/25 08:42:02 [INFO] TLS Enabled
Password: ordererAdminpw
Generating the orderer msp
+ fabric-ca-client enroll -u https://orderer:ordererpw@localhost:9054 --caname ca-orderer -M /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/ordererOrganizations/example.com/orderers/orderer.example.com/msp --tls.certfiles /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/fabric-ca/ordererOrg/ca-cert.pem
2023/10/25 08:42:02 [INFO] TLS Enabled
2023/10/25 08:42:02 [INFO] generating key: &{A:ecdsa S:256}
2023/10/25 08:42:02 [INFO] encoded CSR
2023/10/25 08:42:02 [INFO] Stored client certificate at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/ordererOrganizations/example.com/orderers/orderer.example.com/msp/signcerts/cert.pem
2023/10/25 08:42:02 [INFO] Stored root CA certificate at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/ordererOrganizations/example.com/orderers/orderer.example.com/msp/cacerts/localhost-9054-ca-orderer.pem
2023/10/25 08:42:02 [INFO] Stored Issuer public key at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/ordererOrganizations/example.com/orderers/orderer.example.com/msp/IssuerPublicKey
2023/10/25 08:42:02 [INFO] Stored Issuer revocation public key at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/ordererOrganizations/example.com/orderers/orderer.example.com/msp/IssuerRevocationPublicKey
Generating the orderer-tls certificates, use --csr.hosts to specify Subject Alternative Names
+ fabric-ca-client enroll -u https://orderer:ordererpw@localhost:9054 --caname ca-orderer -M /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/ordererOrganizations/example.com/orderers/orderer.example.com/tls --enrollment.profile tls --csr.hosts orderer.example.com --csr.hosts localhost --tls.certfiles /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/fabric-ca/ordererOrg/ca-cert.pem
2023/10/25 08:42:02 [INFO] TLS Enabled
2023/10/25 08:42:02 [INFO] generating key: &{A:ecdsa S:256}
2023/10/25 08:42:02 [INFO] encoded CSR
2023/10/25 08:42:02 [INFO] Stored client certificate at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/ordererOrganizations/example.com/orderers/orderer.example.com/tls/signcerts/cert.pem
2023/10/25 08:42:02 [INFO] Stored TLS root CA certificate at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/ordererOrganizations/example.com/orderers/orderer.example.com/tls/tlscacerts/tls-localhost-9054-ca-orderer.pem
2023/10/25 08:42:02 [INFO] Stored Issuer public key at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/ordererOrganizations/example.com/orderers/orderer.example.com/tls/IssuerPublicKey
2023/10/25 08:42:02 [INFO] Stored Issuer revocation public key at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/ordererOrganizations/example.com/orderers/orderer.example.com/tls/IssuerRevocationPublicKey
Generating the admin msp
+ fabric-ca-client enroll -u https://ordererAdmin:ordererAdminpw@localhost:9054 --caname ca-orderer -M /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/ordererOrganizations/example.com/users/Admin@example.com/msp --tls.certfiles /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/fabric-ca/ordererOrg/ca-cert.pem
2023/10/25 08:42:02 [INFO] TLS Enabled
2023/10/25 08:42:02 [INFO] generating key: &{A:ecdsa S:256}
2023/10/25 08:42:02 [INFO] encoded CSR
2023/10/25 08:42:02 [INFO] Stored client certificate at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/ordererOrganizations/example.com/users/Admin@example.com/msp/signcerts/cert.pem
2023/10/25 08:42:02 [INFO] Stored root CA certificate at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/ordererOrganizations/example.com/users/Admin@example.com/msp/cacerts/localhost-9054-ca-orderer.pem
2023/10/25 08:42:02 [INFO] Stored Issuer public key at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/ordererOrganizations/example.com/users/Admin@example.com/msp/IssuerPublicKey
2023/10/25 08:42:02 [INFO] Stored Issuer revocation public key at /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/ordererOrganizations/example.com/users/Admin@example.com/msp/IssuerRevocationPublicKey
Generating CCP files for Org1 and Org2
WARN[0000] Found orphan containers ([ca_orderer ca_org1 ca_org2]) for this project. If you removed or renamed this service in your compose file, you can run this command with the --remove-orphans flag to clean it up.
[+] Running 7/7
 ✔ Volume "compose_peer0.org1.example.com"  Created                                                                                                0.0s
 ✔ Volume "compose_peer0.org2.example.com"  Created                                                                                                0.0s
 ✔ Volume "compose_orderer.example.com"     Created                                                                                                0.0s
 ✔ Container orderer.example.com            Started                                                                                                0.0s
 ✔ Container peer0.org1.example.com         Started                                                                                                0.0s
 ✔ Container peer0.org2.example.com         Started                                                                                                0.0s
 ✔ Container cli                            Started                                                                                                0.0s
CONTAINER ID   IMAGE                               COMMAND                  CREATED         STATUS                  PORTS                                                                                                                             NAMES
374fbbf2d9ac   hyperledger/fabric-tools:latest     "/bin/bash"              2 seconds ago   Up Less than a second                                                                                                                                     cli
b562cae99e8b   hyperledger/fabric-peer:latest      "peer node start"        2 seconds ago   Up Less than a second   0.0.0.0:7051->7051/tcp, :::7051->7051/tcp, 0.0.0.0:9444->9444/tcp, :::9444->9444/tcp                                              peer0.org1.example.com
e8d8646f1f4b   hyperledger/fabric-peer:latest      "peer node start"        2 seconds ago   Up Less than a second   0.0.0.0:9051->9051/tcp, :::9051->9051/tcp, 7051/tcp, 0.0.0.0:9445->9445/tcp, :::9445->9445/tcp                                    peer0.org2.example.com
cee0752ac996   hyperledger/fabric-orderer:latest   "orderer"                2 seconds ago   Up Less than a second   0.0.0.0:7050->7050/tcp, :::7050->7050/tcp, 0.0.0.0:7053->7053/tcp, :::7053->7053/tcp, 0.0.0.0:9443->9443/tcp, :::9443->9443/tcp   orderer.example.com
77ef16dfc815   hyperledger/fabric-ca:latest        "sh -c 'fabric-ca-se…"   8 seconds ago   Up 7 seconds            0.0.0.0:9054->9054/tcp, :::9054->9054/tcp, 7054/tcp, 0.0.0.0:19054->19054/tcp, :::19054->19054/tcp                                ca_orderer
ece83d570509   hyperledger/fabric-ca:latest        "sh -c 'fabric-ca-se…"   8 seconds ago   Up 6 seconds            0.0.0.0:7054->7054/tcp, :::7054->7054/tcp, 0.0.0.0:17054->17054/tcp, :::17054->17054/tcp                                          ca_org1
5a5a531ed44a   hyperledger/fabric-ca:latest        "sh -c 'fabric-ca-se…"   8 seconds ago   Up 6 seconds            0.0.0.0:8054->8054/tcp, :::8054->8054/tcp, 7054/tcp, 0.0.0.0:18054->18054/tcp, :::18054->18054/tcp                                ca_org2
Using docker and docker-compose
Generating channel genesis block 'mychannel.block'
Using organization 1
/root/go/src/github.com/b43646/fabric-samples/bin/configtxgen
+ '[' 0 -eq 1 ']'
+ configtxgen -profile ChannelUsingRaft -outputBlock ./channel-artifacts/mychannel.block -channelID mychannel
2023-10-25 08:42:04.723 GMT 0001 INFO [common.tools.configtxgen] main -> Loading configuration
2023-10-25 08:42:04.728 GMT 0002 INFO [common.tools.configtxgen.localconfig] completeInitialization -> orderer type: etcdraft
2023-10-25 08:42:04.729 GMT 0003 INFO [common.tools.configtxgen.localconfig] completeInitialization -> Orderer.EtcdRaft.Options unset, setting to tick_interval:"500ms" election_tick:10 heartbeat_tick:1 max_inflight_blocks:5 snapshot_interval_size:16777216
2023-10-25 08:42:04.729 GMT 0004 INFO [common.tools.configtxgen.localconfig] Load -> Loaded configuration: /root/go/src/github.com/b43646/fabric-samples/test-network/configtx/configtx.yaml
2023-10-25 08:42:04.731 GMT 0005 INFO [common.tools.configtxgen] doOutputBlock -> Generating genesis block
2023-10-25 08:42:04.731 GMT 0006 INFO [common.tools.configtxgen] doOutputBlock -> Creating application channel genesis block
2023-10-25 08:42:04.731 GMT 0007 INFO [common.tools.configtxgen] doOutputBlock -> Writing genesis block
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
2023-10-25 08:42:10.831 GMT 0001 INFO [channelCmd] InitCmdFactory -> Endorser and orderer connections initialized
2023-10-25 08:42:10.855 GMT 0002 INFO [channelCmd] executeJoin -> Successfully submitted proposal to join channel
Joining org2 peer to the channel...
Using organization 2
+ peer channel join -b ./channel-artifacts/mychannel.block
+ res=0
2023-10-25 08:42:13.914 GMT 0001 INFO [channelCmd] InitCmdFactory -> Endorser and orderer connections initialized
2023-10-25 08:42:13.937 GMT 0002 INFO [channelCmd] executeJoin -> Successfully submitted proposal to join channel
Setting anchor peer for org1...
Using organization 1
Fetching channel config for channel mychannel
Using organization 1
Fetching the most recent configuration block for the channel
+ peer channel fetch config config_block.pb -o orderer.example.com:7050 --ordererTLSHostnameOverride orderer.example.com -c mychannel --tls --cafile /opt/gopath/src/github.com/hyperledger/fabric/peer/organizations/ordererOrganizations/example.com/tlsca/tlsca.example.com-cert.pem
2023-10-25 08:42:14.077 UTC 0001 INFO [channelCmd] InitCmdFactory -> Endorser and orderer connections initialized
2023-10-25 08:42:14.080 UTC 0002 INFO [cli.common] readBlock -> Received block: 0
2023-10-25 08:42:14.080 UTC 0003 INFO [channelCmd] fetch -> Retrieving last config block: 0
2023-10-25 08:42:14.081 UTC 0004 INFO [cli.common] readBlock -> Received block: 0
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
2023-10-25 08:42:14.356 UTC 0001 INFO [channelCmd] InitCmdFactory -> Endorser and orderer connections initialized
2023-10-25 08:42:14.370 UTC 0002 INFO [channelCmd] update -> Successfully submitted channel update
Anchor peer set for org 'Org1MSP' on channel 'mychannel'
Setting anchor peer for org2...
Using organization 2
Fetching channel config for channel mychannel
Using organization 2
Fetching the most recent configuration block for the channel
+ peer channel fetch config config_block.pb -o orderer.example.com:7050 --ordererTLSHostnameOverride orderer.example.com -c mychannel --tls --cafile /opt/gopath/src/github.com/hyperledger/fabric/peer/organizations/ordererOrganizations/example.com/tlsca/tlsca.example.com-cert.pem
2023-10-25 08:42:14.506 UTC 0001 INFO [channelCmd] InitCmdFactory -> Endorser and orderer connections initialized
2023-10-25 08:42:14.510 UTC 0002 INFO [cli.common] readBlock -> Received block: 1
2023-10-25 08:42:14.510 UTC 0003 INFO [channelCmd] fetch -> Retrieving last config block: 1
2023-10-25 08:42:14.511 UTC 0004 INFO [cli.common] readBlock -> Received block: 1
+ configtxlator proto_decode --input config_block.pb --type common.Block --output config_block.json
Decoding config block to JSON and isolating config to Org2MSPconfig.json
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
2023-10-25 08:42:14.797 UTC 0001 INFO [channelCmd] InitCmdFactory -> Endorser and orderer connections initialized
2023-10-25 08:42:14.811 UTC 0002 INFO [channelCmd] update -> Successfully submitted channel update
Anchor peer set for org 'Org2MSP' on channel 'mychannel'
Channel 'mychannel' joined
[root@hy test-network]#
[root@hy test-network]# docker ps
CONTAINER ID   IMAGE                               COMMAND                  CREATED          STATUS          PORTS                                                                                                                             NAMES
374fbbf2d9ac   hyperledger/fabric-tools:latest     "/bin/bash"              16 seconds ago   Up 14 seconds                                                                                                                                     cli
b562cae99e8b   hyperledger/fabric-peer:latest      "peer node start"        16 seconds ago   Up 15 seconds   0.0.0.0:7051->7051/tcp, :::7051->7051/tcp, 0.0.0.0:9444->9444/tcp, :::9444->9444/tcp                                              peer0.org1.example.com
e8d8646f1f4b   hyperledger/fabric-peer:latest      "peer node start"        16 seconds ago   Up 14 seconds   0.0.0.0:9051->9051/tcp, :::9051->9051/tcp, 7051/tcp, 0.0.0.0:9445->9445/tcp, :::9445->9445/tcp                                    peer0.org2.example.com
cee0752ac996   hyperledger/fabric-orderer:latest   "orderer"                16 seconds ago   Up 14 seconds   0.0.0.0:7050->7050/tcp, :::7050->7050/tcp, 0.0.0.0:7053->7053/tcp, :::7053->7053/tcp, 0.0.0.0:9443->9443/tcp, :::9443->9443/tcp   orderer.example.com
77ef16dfc815   hyperledger/fabric-ca:latest        "sh -c 'fabric-ca-se…"   22 seconds ago   Up 21 seconds   0.0.0.0:9054->9054/tcp, :::9054->9054/tcp, 7054/tcp, 0.0.0.0:19054->19054/tcp, :::19054->19054/tcp                                ca_orderer
ece83d570509   hyperledger/fabric-ca:latest        "sh -c 'fabric-ca-se…"   22 seconds ago   Up 20 seconds   0.0.0.0:7054->7054/tcp, :::7054->7054/tcp, 0.0.0.0:17054->17054/tcp, :::17054->17054/tcp                                          ca_org1
5a5a531ed44a   hyperledger/fabric-ca:latest        "sh -c 'fabric-ca-se…"   22 seconds ago   Up 20 seconds   0.0.0.0:8054->8054/tcp, :::8054->8054/tcp, 7054/tcp, 0.0.0.0:18054->18054/tcp, :::18054->18054/tcp                                ca_org2
[root@hy test-network]#
[root@hy test-network]#
[root@hy test-network]# ./network.sh deployCC -ccn basic -ccp ../asset-transfer-basic/chaincode-go/ -ccl go
Using docker and docker-compose
deploying chaincode on channel 'mychannel'
executing with the following
- CHANNEL_NAME: mychannel
- CC_NAME: basic
- CC_SRC_PATH: ../asset-transfer-basic/chaincode-go/
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
- CC_SRC_PATH: ../asset-transfer-basic/chaincode-go/
- CC_SRC_LANGUAGE: go
- CC_VERSION: 1.0.1
Vendoring Go dependencies at ../asset-transfer-basic/chaincode-go/
~/go/src/github.com/b43646/fabric-samples/asset-transfer-basic/chaincode-go ~/go/src/github.com/b43646/fabric-samples/test-network
~/go/src/github.com/b43646/fabric-samples/test-network
Finished vendoring Go dependencies
+ '[' false = true ']'
+ peer lifecycle chaincode package basic.tar.gz --path ../asset-transfer-basic/chaincode-go/ --lang golang --label basic_1.0.1
+ res=0
Chaincode is packaged
Installing chaincode on peer0.org1...
Using organization 1
+ peer lifecycle chaincode queryinstalled --output json
+ jq -r 'try (.installed_chaincodes[].package_id)'
+ grep '^basic_1.0.1:e17d781a1fdd39cc251c287e99c6cbcf94867e099e737ee9158223371bb246dc$'
+ test 1 -ne 0
+ peer lifecycle chaincode install basic.tar.gz
+ res=0
2023-10-25 08:47:52.164 GMT 0001 INFO [cli.lifecycle.chaincode] submitInstallProposal -> Installed remotely: response:<status:200 payload:"\nLbasic_1.0.1:e17d781a1fdd39cc251c287e99c6cbcf94867e099e737ee9158223371bb246dc\022\013basic_1.0.1" >
2023-10-25 08:47:52.165 GMT 0002 INFO [cli.lifecycle.chaincode] submitInstallProposal -> Chaincode code package identifier: basic_1.0.1:e17d781a1fdd39cc251c287e99c6cbcf94867e099e737ee9158223371bb246dc
Chaincode is installed on peer0.org1
Install chaincode on peer0.org2...
Using organization 2
+ peer lifecycle chaincode queryinstalled --output json
+ jq -r 'try (.installed_chaincodes[].package_id)'
+ grep '^basic_1.0.1:e17d781a1fdd39cc251c287e99c6cbcf94867e099e737ee9158223371bb246dc$'
+ test 1 -ne 0
+ peer lifecycle chaincode install basic.tar.gz
+ res=0
2023-10-25 08:48:18.165 GMT 0001 INFO [cli.lifecycle.chaincode] submitInstallProposal -> Installed remotely: response:<status:200 payload:"\nLbasic_1.0.1:e17d781a1fdd39cc251c287e99c6cbcf94867e099e737ee9158223371bb246dc\022\013basic_1.0.1" >
2023-10-25 08:48:18.165 GMT 0002 INFO [cli.lifecycle.chaincode] submitInstallProposal -> Chaincode code package identifier: basic_1.0.1:e17d781a1fdd39cc251c287e99c6cbcf94867e099e737ee9158223371bb246dc
Chaincode is installed on peer0.org2
++ peer lifecycle chaincode querycommitted --channelID mychannel --name basic
++ sed -n '/Version:/{s/.*Sequence: //; s/, Endorsement Plugin:.*$//; p;}'
Error: query failed with status: 404 - namespace basic is not defined
+ COMMITTED_CC_SEQUENCE=
+ res=0
Using organization 1
+ peer lifecycle chaincode queryinstalled --output json
+ jq -r 'try (.installed_chaincodes[].package_id)'
+ grep '^basic_1.0.1:e17d781a1fdd39cc251c287e99c6cbcf94867e099e737ee9158223371bb246dc$'
+ res=0
basic_1.0.1:e17d781a1fdd39cc251c287e99c6cbcf94867e099e737ee9158223371bb246dc
Query installed successful on peer0.org1 on channel
Using organization 1
+ peer lifecycle chaincode approveformyorg -o localhost:7050 --ordererTLSHostnameOverride orderer.example.com --tls --cafile /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/ordererOrganizations/example.com/tlsca/tlsca.example.com-cert.pem --channelID mychannel --name basic --version 1.0.1 --package-id basic_1.0.1:e17d781a1fdd39cc251c287e99c6cbcf94867e099e737ee9158223371bb246dc --sequence 1
+ res=0
2023-10-25 08:48:20.378 GMT 0001 INFO [chaincodeCmd] ClientWait -> txid [60d53dcd07e4e31ccf2998c35701234a042035b4ed03af96c22ef7420da01398] committed with status (VALID) at localhost:7051
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
+ peer lifecycle chaincode approveformyorg -o localhost:7050 --ordererTLSHostnameOverride orderer.example.com --tls --cafile /root/go/src/github.com/b43646/fabric-samples/test-network/organizations/ordererOrganizations/example.com/tlsca/tlsca.example.com-cert.pem --channelID mychannel --name basic --version 1.0.1 --package-id basic_1.0.1:e17d781a1fdd39cc251c287e99c6cbcf94867e099e737ee9158223371bb246dc --sequence 1
+ res=0
2023-10-25 08:48:28.593 GMT 0001 INFO [chaincodeCmd] ClientWait -> txid [92cc33ae420b87d5d1c936bc9d3029b84c3c57ff46d4dea810d6162281204ad9] committed with status (VALID) at localhost:9051
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
2023-10-25 08:48:37.043 GMT 0001 INFO [chaincodeCmd] ClientWait -> txid [6d436fe4fc23bd94b057b9e13e9ac553b8ba1153dd617705aff8f561aa5fb45b] committed with status (VALID) at localhost:7051
2023-10-25 08:48:37.046 GMT 0002 INFO [chaincodeCmd] ClientWait -> txid [6d436fe4fc23bd94b057b9e13e9ac553b8ba1153dd617705aff8f561aa5fb45b] committed with status (VALID) at localhost:9051
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
[root@hy test-network]# cd ../asset-transfer-basic/application-g
application-gateway-go/         application-gateway-java/       application-gateway-typescript/ application-go/
[root@hy test-network]# cd ../asset-transfer-basic/application-gateway-
application-gateway-go/         application-gateway-java/       application-gateway-typescript/
[root@hy test-network]# cd ../asset-transfer-basic/application-gateway-go/
[root@hy application-gateway-go]# ls
assetTransfer.go  go.mod  go.sum
[root@hy application-gateway-go]# vi assetTransfer.go
[root@hy application-gateway-go]# GO111MODULE=on go mod vendor
go: downloading github.com/hyperledger/fabric-gateway v1.2.2
go: downloading github.com/hyperledger/fabric-protos-go-apiv2 v0.2.0
go: downloading google.golang.org/genproto v0.0.0-20230216225411-c8e22ba71e44
go: downloading github.com/miekg/pkcs11 v1.1.1
[root@hy application-gateway-go]# vi ../application-gateway-typescript/
.eslintrc.json  .gitignore      .npmrc          package.json    src/            tsconfig.json
[root@hy application-gateway-go]# vi ../application-gateway-typescript/src/app.ts
[root@hy application-gateway-go]# vi ../application-
application-gateway-go/         application-gateway-typescript/ application-java/               application-typescript/
application-gateway-java/       application-go/                 application-javascript/         application-typescript-hsm/
[root@hy application-gateway-go]# vi ../application-typescript
application-typescript/     application-typescript-hsm/
[root@hy application-gateway-go]# vi ../application-typescript/
.gitignore     package.json   src/           tsconfig.json  tslint.json
[root@hy application-gateway-go]# vi ../application-typescript/src/
app.ts  utils/
[root@hy application-gateway-go]# vi ../application-typescript/src/app.ts
[root@hy application-gateway-go]# ls
assetTransfer.go  go.mod  go.sum  vendor
[root@hy application-gateway-go]# vi assetTransfer.go
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
[root@hy application-gateway-go]# vi
assetTransfer.go  go.mod            go.sum            vendor/
[root@hy application-gateway-go]# vi assetTransfer.go


```
