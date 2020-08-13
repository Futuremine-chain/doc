# RPC 文档

## 介绍
GRPC实现
* go语言调用，使用现有的[Client](https://github.com/Futuremine-chain/futuremine/blob/master/futuremine/rpc/rpcclient.go)
* 其他语言，使用[proto文件](https://github.com/Futuremine-chain/futuremine/blob/master/futuremine/rpc/rpc.proto)生成rpcclient

## 目录

### GetAccount
- info：获取账户信息
- agrs：address(json bytes)
```json
["xC2xC5DNc3Uz3jMnufsX9jX8a67mypdfxGH"]
```
- result:
    
```json
{
    "address": "xC3LLtxiCaAcG2KrJmzo75pdavgqNLooz1N",
    "nonce": 9,
    "tokens": [
        {
            "address": "FMC",
            "balance": 129280.2198,
            "locked": 10
        }
    ],
    "confirmed": 116836
}
```

### SendMessageRaw
- info：发送消息
- agrs：[RpcMessage(json bytes)](https://github.com/Futuremine-chain/futuremine/blob/master/futuremine/rpc/types/message.go)

### GetMessage
- info：获取消息
- agrs：msghash(json bytes)
```json
["0x0131fe37c33751a1284c4d82c8698cbae3a912464aeddb5d9b54457f27e1da94"]
```
- result:
    
```json
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
```

### GetBlockHash
- info：获取block
- agrs：blockhash(json bytes)
```json
["0xcf7e0229a8c89c01ef185d3bd874267540d79cb9c4d6882d1cdadfeab03ec585"]
```
- result:
    
```json
{
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
    "confirmed": true 
}
```
### GetBlockHeight
- info：获取block
- agrs：blockheight(json bytes)
```json
[10]
```
- result:
    
```json
{
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
    "confirmed": true 
}
```

### LastHeight
- info：获取最高高度
- agrs：无
- result: 高度(string bytes)

### Confirmed
- info：获取已经确认的最高区块高度
- agrs：无
- result: 高度(string bytes)

### GetMsgPool
- info：获取消息池消息
- agrs：无
- result: 高度(string bytes)
```json
{
    "msgs": 1,
    "ready": 1,
    "cache": 0,
    "readymsgs": [ 
        {
            "msgheader": {
                "msghash": "0x0131fe37c33751a1284c4d82c8698cbae3a912464aeddb5d9b54457f27e1da94",
                "type": 4,
                "from": "xC2xC5DNc3Uz3jMnufsX9jX8a67mypdfxGH",
                "nonce": 6,
                "fee": 10000000,
                "time": 1597283126,
                "signscript": {
                    "signature": "3045022100fe60cf4ab15d6350796f74ee7d9c7c5397de0b12e488129a90b9b810c5acfd35022024c3cad109e054b3ab1174564ffb7686105ae5e4c79bbdf288c009d857661af8",
                    "pubkey": "0308917998ee6b83ea8f8d3afc2888865233646e3db02de2d792f554b0981ade4b"
                }
            },
            "msgbody": {
                "to": "xC2xC5DNc3Uz3jMnufsX9jX8a67mypdfxGH"
            }
        }
    ],
    "cachemsgs": null
}
```

### Candidates
- info：获取候选人信息
- agrs：无
- result: [RpcCandidates(json bytes)](https://github.com/Futuremine-chain/futuremine/blob/master/futuremine/rpc/types/candiates.go)
```json
{
    "members": [
        {
            "address": "xBzSZn52pNuBsUhu3qnRYTqo8HetVpgrRVL",
            "peerid": "16Uiu2HAmHBNYs8eFMnjpUwoJzCws77B8LuSXqVwKaQXcA3WVDvvQ",
            "votes": 14668501790000,
            "mntcount": 0
        },
        {
            "address": "xC1cGYmjAEU3yymozKs5jPLQPzkyzbvxJuU",
            "peerid": "16Uiu2HAmLk1r8BHEpuTR9XRm1DCw5GpqaANF2RYJ3DRzQxtAtSc9",
            "votes": 14791500940000,
            "mntcount": 0
        },
        {
            "address": "xC2xC5DNc3Uz3jMnufsX9jX8a67mypdfxGH",
            "peerid": "16Uiu2HAmDESGfzayFiBKnKaryyVgXKmJvePva8nFVNzFsGKkLdW2",
            "votes": 14680013370000,
            "mntcount": 0
        },
        {
            "address": "xC3LLtxiCaAcG2KrJmzo75pdavgqNLooz1N",
            "peerid": "16Uiu2HAmSUvLmVizqJYNraZ5DUQQGHCgDL6XvRgoTj9KY9oEZoba",
            "votes": 14668021980000,
            "mntcount": 0
        },
        {
            "address": "xC554Aq8EiCz82hzVfi5PmnLCFGxAi9fBMp",
            "peerid": "16Uiu2HAm9KiJJfE8mhwFuLv8Yco1YJkFtMekzUPowMW4t8FeLbw7",
            "votes": 14659014950000,
            "mntcount": 0
        },
        {
            "address": "xC6nGfqHPt4KPoyhwCG3zNemNweYsBWXRR2",
            "peerid": "16Uiu2HAkvG7xGvVZBkZR16sWwmqhqGNm69FSa61tbpphpgCcMmEo",
            "votes": 14839012040000,
            "mntcount": 0
        },
        {
            "address": "xC86k2HFGPzsJ1vubBoR7DXviN6UKpEKFRv",
            "peerid": "16Uiu2HAm5VouADKhW55qLBiFoixegEtym72C9P6M2XKZ7bEMNUt8",
            "votes": 14675493730000,
            "mntcount": 0
        },
        {
            "address": "xC8hzrNRzMzpUcs68HcWqFTLBjWKeTatqcJ",
            "peerid": "16Uiu2HAm92KMJiSLAYFCc7AdTBFwVgCBJ9zhWYU6UHM5vMAWH1hr",
            "votes": 14838509100000,
            "mntcount": 0
        },
        {
            "address": "xCJVPCgbiRy6tAtozAZwXLF5NzG9XBU16ou",
            "peerid": "16Uiu2HAkyexJCRYMHrN2Ft3E5MmJr3eoNtEZNJjaZ4jbwXcA1FCK",
            "votes": 14652492100000,
            "mntcount": 0
        }
    ]
}
```

### GetCycleSupers
- info：获取某周期的超级节点信息
- agrs：cycle(json bytes)
```json
[18487]
```
- result:
```json
{
    "members": [
        {
            "address": "xBzSZn52pNuBsUhu3qnRYTqo8HetVpgrRVL",
            "peerid": "16Uiu2HAmHBNYs8eFMnjpUwoJzCws77B8LuSXqVwKaQXcA3WVDvvQ",
            "votes": 14494501760000,
            "mntcount": 179 
        },
        {
            "address": "xC3LLtxiCaAcG2KrJmzo75pdavgqNLooz1N",
            "peerid": "16Uiu2HAmSUvLmVizqJYNraZ5DUQQGHCgDL6XvRgoTj9KY9oEZoba",
            "votes": 14494021980000,
            "mntcount": 179
        },
        {
            "address": "xC2xC5DNc3Uz3jMnufsX9jX8a67mypdfxGH",
            "peerid": "16Uiu2HAmDESGfzayFiBKnKaryyVgXKmJvePva8nFVNzFsGKkLdW2",
            "votes": 14506012370000,
            "mntcount": 179
        },
        {
            "address": "xC554Aq8EiCz82hzVfi5PmnLCFGxAi9fBMp",
            "peerid": "16Uiu2HAm9KiJJfE8mhwFuLv8Yco1YJkFtMekzUPowMW4t8FeLbw7",
            "votes": 14485003950000,
            "mntcount": 179
        },
        {
            "address": "xCJVPCgbiRy6tAtozAZwXLF5NzG9XBU16ou",
            "peerid": "16Uiu2HAkyexJCRYMHrN2Ft3E5MmJr3eoNtEZNJjaZ4jbwXcA1FCK",
            "votes": 14478502100000,
            "mntcount": 180
        },
        {
            "address": "xC8hzrNRzMzpUcs68HcWqFTLBjWKeTatqcJ",
            "peerid": "16Uiu2HAm92KMJiSLAYFCc7AdTBFwVgCBJ9zhWYU6UHM5vMAWH1hr",
            "votes": 14665011100000,
            "mntcount": 180
        },
        {
            "address": "xC6nGfqHPt4KPoyhwCG3zNemNweYsBWXRR2",
            "peerid": "16Uiu2HAkvG7xGvVZBkZR16sWwmqhqGNm69FSa61tbpphpgCcMmEo",
            "votes": 14664502070000,
            "mntcount": 180
        },
        {
            "address": "xC86k2HFGPzsJ1vubBoR7DXviN6UKpEKFRv",
            "peerid": "16Uiu2HAm5VouADKhW55qLBiFoixegEtym72C9P6M2XKZ7bEMNUt8",
            "votes": 14501503730000,
            "mntcount": 180
        },
        {
            "address": "xC1cGYmjAEU3yymozKs5jPLQPzkyzbvxJuU",
            "peerid": "16Uiu2HAmLk1r8BHEpuTR9XRm1DCw5GpqaANF2RYJ3DRzQxtAtSc9",
            "votes": 14617500940000,
            "mntcount": 179
        }
    ]
}
```

### Token
- info：获取token详情
- agrs：token地址(string bytes)
- result:
```json
{
    "address": "TfUvuDSJHWKVUZ93PwJf5xddKokaWvJMU61",
    "sender": "xCJVPCgbiRy6tAtozAZwXLF5NzG9XBU16ou",
    "name": "kj",
    "shorthand": "HHC",
    "records": [
        {
            "height": 132644,
            "receiver": "xC5txx2jwPikH1prBqzuJVBS4VGDbYUhdBw",
            "msghash": "0x7b8fd5831e6108f2b63d33e97e66f72c28ed0ca11c6652571054270b86551a0d",
            "time": 1597285354,
            "amount": 100000
        },
        {
            "height": 132689,
            "receiver": "xC5txx2jwPikH1prBqzuJVBS4VGDbYUhdBw",
            "msghash": "0xee46354fbf4ec59b688365207440ca1f331c7f604f4d7873ea0885e6d6227093",
            "time": 1597285579,
            "amount": 100000
        }
    ]
}
```

### PeersInfo
- info：获取p2p节点信息
- agrs：无
- result:
```json
[
    {
        "version": "0.1.1",
        "network": "testnet",
        "peer": "16Uiu2HAm9YPWTdzZ3F8sUmQPzg1g8PsaRXT1CNbX6XuccKijk1cn",
        "address": "{16Uiu2HAm9YPWTdzZ3F8sUmQPzg1g8PsaRXT1CNbX6XuccKijk1cn: [/ip4/172.31.55.102/tcp/18911 /ip4/8.210.109.13/tcp/18911]}",
        "connections": 11,
        "messages": 0,
        "height": 132697,
        "confirmed": 132690
    },
    {
        "version": "0.1.1",
        "network": "testnet",
        "peer": "16Uiu2HAmDESGfzayFiBKnKaryyVgXKmJvePva8nFVNzFsGKkLdW2",
        "address": "{16Uiu2HAmDESGfzayFiBKnKaryyVgXKmJvePva8nFVNzFsGKkLdW2: [/ip4/172.31.55.104/tcp/19164 /ip4/8.210.100.179/tcp/19164]}",
        "connections": 11,
        "messages": 0,
        "height": 132697,
        "confirmed": 132690
    },
    {
        "version": "0.1.1",
        "network": "testnet",
        "peer": "16Uiu2HAm5VouADKhW55qLBiFoixegEtym72C9P6M2XKZ7bEMNUt8",
        "address": "{16Uiu2HAm5VouADKhW55qLBiFoixegEtym72C9P6M2XKZ7bEMNUt8: [/ip4/172.31.55.103/tcp/19166 /ip4/8.210.251.205/tcp/19166]}",
        "connections": 11,
        "messages": 0,
        "height": 132697,
        "confirmed": 132690
    },
    {
        "version": "0.1.1",
        "network": "testnet",
        "peer": "16Uiu2HAmSUvLmVizqJYNraZ5DUQQGHCgDL6XvRgoTj9KY9oEZoba",
        "address": "{16Uiu2HAmSUvLmVizqJYNraZ5DUQQGHCgDL6XvRgoTj9KY9oEZoba: [/ip4/172.31.55.104/tcp/19162 /ip4/8.210.100.179/tcp/19162]}",
        "connections": 11,
        "messages": 0,
        "height": 132697,
        "confirmed": 132690
    },
    {
        "version": "0.1.1",
        "network": "testnet",
        "peer": "16Uiu2HAkvG7xGvVZBkZR16sWwmqhqGNm69FSa61tbpphpgCcMmEo",
        "address": "{16Uiu2HAkvG7xGvVZBkZR16sWwmqhqGNm69FSa61tbpphpgCcMmEo: [/ip4/172.31.55.104/tcp/19160 /ip4/8.210.100.179/tcp/19160]}",
        "connections": 11,
        "messages": 0,
        "height": 132697,
        "confirmed": 132690
    },
    {
        "version": "0.1.1",
        "network": "testnet",
        "peer": "16Uiu2HAkyexJCRYMHrN2Ft3E5MmJr3eoNtEZNJjaZ4jbwXcA1FCK",
        "address": "{16Uiu2HAkyexJCRYMHrN2Ft3E5MmJr3eoNtEZNJjaZ4jbwXcA1FCK: [/ip4/172.31.55.104/tcp/19166 /ip4/8.210.100.179/tcp/19166]}",
        "connections": 11,
        "messages": 0,
        "height": 132697,
        "confirmed": 132690
    },
    {
        "version": "0.1.1",
        "network": "testnet",
        "peer": "16Uiu2HAmHBNYs8eFMnjpUwoJzCws77B8LuSXqVwKaQXcA3WVDvvQ",
        "address": "{16Uiu2HAmHBNYs8eFMnjpUwoJzCws77B8LuSXqVwKaQXcA3WVDvvQ: [/ip4/172.31.55.103/tcp/19160 /ip4/8.210.251.205/tcp/19160]}",
        "connections": 11,
        "messages": 0,
        "height": 132697,
        "confirmed": 132690
    },
    {
        "version": "0.1.1",
        "network": "testnet",
        "peer": "16Uiu2HAm92KMJiSLAYFCc7AdTBFwVgCBJ9zhWYU6UHM5vMAWH1hr",
        "address": "{16Uiu2HAm92KMJiSLAYFCc7AdTBFwVgCBJ9zhWYU6UHM5vMAWH1hr: [/ip4/172.31.55.103/tcp/19162 /ip4/8.210.251.205/tcp/19162]}",
        "connections": 11,
        "messages": 0,
        "height": 132697,
        "confirmed": 132690
    },
    {
        "version": "0.1.1",
        "network": "testnet",
        "peer": "16Uiu2HAm9KiJJfE8mhwFuLv8Yco1YJkFtMekzUPowMW4t8FeLbw7",
        "address": "{16Uiu2HAm9KiJJfE8mhwFuLv8Yco1YJkFtMekzUPowMW4t8FeLbw7: [/ip4/172.31.55.103/tcp/19168 /ip4/8.210.251.205/tcp/19168]}",
        "connections": 11,
        "messages": 0,
        "height": 132697,
        "confirmed": 132690
    },
    {
        "version": "0.1.1",
        "network": "testnet",
        "peer": "16Uiu2HAmLk1r8BHEpuTR9XRm1DCw5GpqaANF2RYJ3DRzQxtAtSc9",
        "address": "{16Uiu2HAmLk1r8BHEpuTR9XRm1DCw5GpqaANF2RYJ3DRzQxtAtSc9: [/ip4/172.31.55.103/tcp/19164 /ip4/8.210.251.205/tcp/19164]}",
        "connections": 11,
        "messages": 0,
        "height": 132697,
        "confirmed": 132690
    }
]
```
### LocalInfo
- info：获取本地节点信息
- agrs：无
- result:
```json
{
    "version": "0.1.1",
    "network": "testnet",
    "peer": "16Uiu2HAmKxk5CqxsZWU5RtCNPMm6nsj1zjJYYuoVbPNQNpBPoj2B",
    "address": "{16Uiu2HAmKxk5CqxsZWU5RtCNPMm6nsj1zjJYYuoVbPNQNpBPoj2B: [/ip4/192.168.31.140/tcp/19160 /ip4/0.0.0.0/tcp/19160]}",
    "connections": 10,
    "messages": 1,
    "height": 132729,
    "confirmed": 132722
}
```