# RPC 文档

## 介绍
GRPC实现，[proto文件](https://github.com/Futuremine-chain/futuremine/blob/master/futuremine/rpc/rpc.proto)

## 目录

* GetAccount
	- info：获取账户信息
	- agrs：
```json
				[address]
```
	- result:
```json
	{
    "address": "xC3LLtxiCaAcG2KrJmzo75pdavgqNLooz1N",//地址
    "nonce": 9,//账户nonce，
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

* SendMessageRaw
* GetMessage
* GetBlockHash
* GetBlockHeight
* LastHeight
* Confirmed
* GetMsgPool
* Candidates
* GetCycleSupers
* Token
* PeersInfo
* LocalInfo