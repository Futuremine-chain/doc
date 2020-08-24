# Message 文档

## 目录
### 类型
* Transaction 发送交易
* Token 发布代币
* Candidate 成为候选人
* Cancel 取消候选
* Vote 投票

### 一 通过kit库创建发送消息
```
github.com/Futuremine-chain/future/future/common/kit/message
github.com/Futuremine-chain/future/future/common/kit
github.com/Futuremine-chain/future/tools/arry
github.com/Futuremine-chain/future/common/param
github.com/Futuremine-chain/future/future/rpc/types
github.com/Futuremine-chain/future/future/rpc
```


#### 创建交易
```
from := "xCJVPCgbiRy6tAtozAZwXLF5NzG9XBU16ou"
to := "xC8hzrNRzMzpUcs68HcWqFTLBjWKeTatqcJ"
token := "TfUvuDSJHWKVUZ93PwJf5xddKokaWvJMU61"
msg := message.NewTransaction(from, to, token, amount, 1000000, 1)
```

#### 创建代币
```
from := "xCJVPCgbiRy6tAtozAZwXLF5NzG9XBU16ou"
to := "xC8hzrNRzMzpUcs68HcWqFTLBjWKeTatqcJ"
coinAbbr := "TC"
coinName := "TEST COIN"
tokenAddr := kit.GenerateTokenAddress(param.MainNet, from, coinAbbr)
msg := message.NewToken(from, to, tokenAddr , 1000000000000000, 1000000, 1, coinName, coinAbbr)
```

#### 创建候选人
```
from := "xCJVPCgbiRy6tAtozAZwXLF5NzG9XBU16ou"
peerId := "16Uiu2HAm92KMJiSLAYFCc7AdTBFwVgCBJ9zhWYU6UHM5vMAWH1hr"
msg := message.NewCandidate(from, peerStr, 1000000, 1)
```

#### 创建取消候选人
```
from := "xCJVPCgbiRy6tAtozAZwXLF5NzG9XBU16ou"
msg := message.NewCancel(from, 1000000, 1)
```

#### 创建投票
```
from := "xCJVPCgbiRy6tAtozAZwXLF5NzG9XBU16ou"
to := "xC6nGfqHPt4KPoyhwCG3zNemNweYsBWXRR2"
msg := message.NewVote(from, to, 1000000, 1)
```

#### 消息签名
```
msg.SignMsg(private)
```

#### 发送消息

```
rpcMsg := types.MsgToRpcMsg(msg)
jsonBytes, _ := json.Marshal(rpcMsg)
req := &rpc.Request{Params: jsonBytes}
ctx, _ := context.WithTimeout(context.TODO(), time.Second*20)
resp, err := rpcClient.SendMessageRaw(ctx, req)
```

### 二 通过rpc创建发送消息

#### 创建交易
```
// 创建交易，拿到交易hash
ti := uint64(time.Now().Unix())
resp, err := client.Gc.CreateTransaction(context.Background(), &TransactionReq{
    From:      "FMejc9bjiTeQzKQG9fSDPGdsRzzEdEQe6se",
    To:        "FMegukTco2m1S9Y4ebXM9kVpQ6jqGGZBwWv",
    Token:     "FM",
    Amount:    1000000000,
    Fees:      1000000,
    Nonce:     3,
    Timestamp: ti,
})

// 离线签名交易hash(js or go)
signature, err := message.Sign(hash)

// 发送签名后的交易信息
resp, err = client.Gc.SendTransaction(context.Background(), &TransactionReq{
    From:      "FMejc9bjiTeQzKQG9fSDPGdsRzzEdEQe6se",
    To:        "FMegukTco2m1S9Y4ebXM9kVpQ6jqGGZBwWv",
    Token:     "FM",
    Amount:    1000000000,
    Fees:      1000000,
    Nonce:     8,
    Timestamp: ti,
    Signature: signature.SignatureString(),
    Publickey: signature.PubKeyString(),
})
```

#### 创建代币
```
ti := uint64(time.Now().Unix())
// 生成代币地址
resp, err := client.Gc.GenerateTokenAddress(context.Background(), &GenerateTokenReq{
    Network: "mainnet",
    Address: "FMejc9bjiTeQzKQG9fSDPGdsRzzEdEQe6se",
    Abbr:    "ANBJ",
})

// 创建代币消息，拿到消息hash
resp, err = client.Gc.CreateToken(context.Background(), &TokenReq{
    From:      "FMejc9bjiTeQzKQG9fSDPGdsRzzEdEQe6se",
    Receiver:  "FMegukTco2m1S9Y4ebXM9kVpQ6jqGGZBwWv",
    Token:     token,
    Amount:    1000000000000,
    Fees:      1000000,
    Nonce:     4,
    Name:      "12121",
    Abbr:      "ANBJ",
    Increase:  true,
    Timestamp: ti,
})

// 离线签名消息hash(js or go)
signature, err := message.Sign(hash)

// 发送签名后的消息信息
resp, err = client.Gc.SendToken(context.Background(), &TokenReq{
		From:      "FMejc9bjiTeQzKQG9fSDPGdsRzzEdEQe6se",
		Receiver:  "FMegukTco2m1S9Y4ebXM9kVpQ6jqGGZBwWv",
		Token:     token,
		Amount:    1000000000000,
		Fees:      1000000,
		Nonce:     4,
		Name:      "12121",
		Abbr:      "ANBJ",
		Increase:  true,
		Timestamp: ti,
		Signature: signature.SignatureString(),
		Publickey: signature.PubKeyString(),
	})
```

#### 创建候选人
```
// 创建候选人消息，拿到消息hash
resp, err := client.Gc.CreateCandidate(context.Background(), &CandidateReq{
    From:      "FMejc9bjiTeQzKQG9fSDPGdsRzzEdEQe6se",
    P2Pid:     "16Uiu2HAkwKrbmaz3WRPjdJZbEBDCj412auZPoBCr3cpDViztzcX6",
    Fees:      1000000,
    Nonce:     5,
    Timestamp: ti,
})

// 离线签名消息hash(js or go)
signature, err := message.Sign(hash)

// 发送签名后的消息信息
resp, err = client.Gc.SendCandidate(context.Background(), &CandidateReq{
    From:      "FMejc9bjiTeQzKQG9fSDPGdsRzzEdEQe6se",
    P2Pid:     "16Uiu2HAkwKrbmaz3WRPjdJZbEBDCj412auZPoBCr3cpDViztzcX6",
    Fees:      1000000,
    Nonce:     5,
    Timestamp: ti,
    Signature: signature.SignatureString(),
    Publickey: signature.PubKeyString(),
})
```

#### 创建取消候选人
```
// 创建取消候选人消息，拿到消息hash
resp, err := client.Gc.CreateCancel(context.Background(), &CancelReq{
    From:      "FMejc9bjiTeQzKQG9fSDPGdsRzzEdEQe6se",
    Fees:      1000000,
    Nonce:     6,
    Timestamp: ti,
})

// 离线签名消息hash(js or go)
signature, err := message.Sign(hash)

// 发送签名后的消息信息
resp, err = client.Gc.SendCancel(context.Background(), &CancelReq{
    From:      "FMejc9bjiTeQzKQG9fSDPGdsRzzEdEQe6se",
    Fees:      1000000,
    Nonce:     6,
    Timestamp: ti,
    Signature: si.SignatureString(),
    Publickey: si.PubKeyString(),
})
```

#### 创建投票
```
// 创建取消候选人消息，拿到消息hash
resp, err := client.Gc.CreateVote(context.Background(), &VoteReq{
    From:      "FMejc9bjiTeQzKQG9fSDPGdsRzzEdEQe6se",
    To:        "FMejc9bjiTeQzKQG9fSDPGdsRzzEdEQe6se",
    Fees:      1000000,
    Nonce:     7,
    Timestamp: ti,
})

// 离线签名消息hash(js or go)
signature, err := message.Sign(hash)

// 发送签名后的消息信息
resp, err = client.Gc.SendVote(context.Background(), &VoteReq{
    From:      "FMejc9bjiTeQzKQG9fSDPGdsRzzEdEQe6se",
    To:        "FMejc9bjiTeQzKQG9fSDPGdsRzzEdEQe6se",
    Fees:      1000000,
    Nonce:     7,
    Timestamp: ti,
    Signature: si.SignatureString(),
    Publickey: si.PubKeyString(),
})
```
