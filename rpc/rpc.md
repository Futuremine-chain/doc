# RPC 文档

## 介绍
GRPC实现，[proto文件](https://github.com/Futuremine-chain/futuremine/blob/master/futuremine/rpc/rpc.proto)

## 目录

### GetAccount
*info：获取账户信息
*agrs：address(json bytes)
```
json[xC2xC5DNc3Uz3jMnufsX9jX8a67mypdfxGH]
```
*result:
    
```
json{
        "address": "xC3LLtxiCaAcG2KrJmzo75pdavgqNLooz1N",//地址
        "nonce": 9,//账户nonce
        "tokens": [
            {
                "address": "FMC",//币地址
                "balance": 129280.2198,//余额
                "locked": 10 //未确认的余额
            }
        ],
        "confirmed": 116836//当前账户确认高度
    }
```

### SendMessageRaw
*info：发送消息
*agrs：[RpcMessage(json bytes)](https://github.com/Futuremine-chain/futuremine/blob/master/futuremine/rpc/types/message.go)

### GetMessage
*info：获取消息
*agrs：msghash(json bytes)
```
json[0x0131fe37c33751a1284c4d82c8698cbae3a912464aeddb5d9b54457f27e1da94]
```
*result:
    
```
json{
        "msgheader": {
            "msghash": "0xfbb7ee1e43045ba62edff7f350017b0c4306eb46c84b90ef15b0ed5a09cf4e62",
            "type": 0,
            "from": "coinbase",
            "nonce": 0,
            "fee": 0,
            "time": 1596604970,
            "signscript": {
                "signature": "",
                "pubkey": ""
            }
        },
        "msgbody": {
            "token": "FMC",
            "to": "xC8hzrNRzMzpUcs68HcWqFTLBjWKeTatqcJ",
            "amount": 1000000000
        }
    }
```

### GetBlockHash
*info：获取block
*agrs：blockhash(json bytes)
```
json[0xcf7e0229a8c89c01ef185d3bd874267540d79cb9c4d6882d1cdadfeab03ec585]
```
*result:
    
```
json{
        "header": {
            "version": 0,
            "hash": "0xcf7e0229a8c89c01ef185d3bd874267540d79cb9c4d6882d1cdadfeab03ec585",
            "parenthash": "0xc16021471765ddedf666b4880a7aa90bb86b2825c28baa602c0d2f3e4141e0b3",
            "txroot": "0x2a4adc46371093423d18c0a49be6fc3de5cabb9d5151e2515bba665804fca131",
            "actroot": "0xbd3a49a4a41f6221bd4ddf36b4d77afe892fcbfa1e8afbec60f6e509a16812d3",
            "tokenroot": "0x56e81f171bcc55a6ff8345e692c0f86e5b48e01b996cadc001622fb5e363b421",
            "dposroot": "0xf850682a3f63117104cca75545fd38640b5a1daa1a8ad2d01a1dafd5326e0332",
            "height": 10,
            "time": "2020-08-05T13:22:50+08:00",
            "cycle": 18479,
            "signer": "xC8hzrNRzMzpUcs68HcWqFTLBjWKeTatqcJ",
            "signature": {
                "signature": "3045022100afcaa6c9224d6a29bc3235408c29293df3117e05b416f3e6be61bd25f8b3b375022048c1ef86f6f4b2f2a749ded98e0e81ef4949d82c9673db5cb409ea4597d30254",
                "pubkey": "02ca07eed74b343f53d505416037f1cb9644d1e67cbc220a7f6ab743f3ebe166b1"
            }
        },
        "body": {
            "transactions": [
                {
                    "msgheader": {
                        "msghash": "0xfbb7ee1e43045ba62edff7f350017b0c4306eb46c84b90ef15b0ed5a09cf4e62",
                        "type": 0,
                        "from": "coinbase",
                        "nonce": 0,
                        "fee": 0,
                        "time": 1596604970,
                        "signscript": {
                            "signature": "",
                            "pubkey": ""
                        }
                    },
                    "msgbody": {
                        "token": "FMC",
                        "to": "xC8hzrNRzMzpUcs68HcWqFTLBjWKeTatqcJ",
                        "amount": 1000000000
                    }
                }
            ]
        },
        "confirmed": true //是否已确认
    }
```
### GetBlockHeight
*info：获取block
*agrs：blockheight(json bytes)
```
json[10]
```
*result:
    
```
json{
        "header": {
            "version": 0,
            "hash": "0xcf7e0229a8c89c01ef185d3bd874267540d79cb9c4d6882d1cdadfeab03ec585",
            "parenthash": "0xc16021471765ddedf666b4880a7aa90bb86b2825c28baa602c0d2f3e4141e0b3",
            "txroot": "0x2a4adc46371093423d18c0a49be6fc3de5cabb9d5151e2515bba665804fca131",
            "actroot": "0xbd3a49a4a41f6221bd4ddf36b4d77afe892fcbfa1e8afbec60f6e509a16812d3",
            "tokenroot": "0x56e81f171bcc55a6ff8345e692c0f86e5b48e01b996cadc001622fb5e363b421",
            "dposroot": "0xf850682a3f63117104cca75545fd38640b5a1daa1a8ad2d01a1dafd5326e0332",
            "height": 10,
            "time": "2020-08-05T13:22:50+08:00",
            "cycle": 18479,
            "signer": "xC8hzrNRzMzpUcs68HcWqFTLBjWKeTatqcJ",
            "signature": {
                "signature": "3045022100afcaa6c9224d6a29bc3235408c29293df3117e05b416f3e6be61bd25f8b3b375022048c1ef86f6f4b2f2a749ded98e0e81ef4949d82c9673db5cb409ea4597d30254",
                "pubkey": "02ca07eed74b343f53d505416037f1cb9644d1e67cbc220a7f6ab743f3ebe166b1"
            }
        },
        "body": {
            "transactions": [
                {
                    "msgheader": {
                        "msghash": "0xfbb7ee1e43045ba62edff7f350017b0c4306eb46c84b90ef15b0ed5a09cf4e62",
                        "type": 0,
                        "from": "coinbase",
                        "nonce": 0,
                        "fee": 0,
                        "time": 1596604970,
                        "signscript": {
                            "signature": "",
                            "pubkey": ""
                        }
                    },
                    "msgbody": {
                        "token": "FMC",
                        "to": "xC8hzrNRzMzpUcs68HcWqFTLBjWKeTatqcJ",
                        "amount": 1000000000
                    }
                }
            ]
        },
        "confirmed": true //是否已确认
    }
```

### LastHeight
*info：获取最高高度
*agrs：无
*result: 高度(string bytes)

### Confirmed
### GetMsgPool
### Candidates
### GetCycleSupers
### Token
### PeersInfo
### LocalInfo