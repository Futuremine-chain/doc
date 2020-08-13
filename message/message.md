# Message 文档

## 目录
### 类型
* Transaction 发送交易
* Token 发布代币
* Candidate 成为候选人
* Cancel 取消候选
* Vote 投票

### 工具包
```
github.com/Futuremine-chain/futuremine/futuremine/common/kit/message
github.com/Futuremine-chain/futuremine/futuremine/common/kit
github.com/Futuremine-chain/futuremine/tools/arry
github.com/Futuremine-chain/futuremine/common/param
github.com/Futuremine-chain/futuremine/futuremine/rpc/types
github.com/Futuremine-chain/futuremine/futuremine/rpc
```

### 创建交易
```
from := arry.StringToAddress("xCJVPCgbiRy6tAtozAZwXLF5NzG9XBU16ou")
to := arry.StringToAddress("xC8hzrNRzMzpUcs68HcWqFTLBjWKeTatqcJ")
token := arry.StringToAddress("TfUvuDSJHWKVUZ93PwJf5xddKokaWvJMU61")
msg := message.NewTransaction(from, to, token, amount, 1000000, 1)
```

### 创建代币
```
from := arry.StringToAddress("xCJVPCgbiRy6tAtozAZwXLF5NzG9XBU16ou")
to := arry.StringToAddress("xC8hzrNRzMzpUcs68HcWqFTLBjWKeTatqcJ")
coinAbbr := "TC"
coinName := "TEST COIN"
tokenAddr := kit.GenerateTokenAddress(param.MainNet, from, coinAbbr)
msg := message.NewToken(from, to, tokenAddr , 1000000000000000, 1000000, 1, coinName, coinAbbr)
```

### 创建候选人
```
from := arry.StringToAddress("xCJVPCgbiRy6tAtozAZwXLF5NzG9XBU16ou")
peerId := "16Uiu2HAm92KMJiSLAYFCc7AdTBFwVgCBJ9zhWYU6UHM5vMAWH1hr"
msg := message.NewCandidate(from, peerStr, 1000000, 1)
```

### 创建取消候选人
```
from := arry.StringToAddress("xCJVPCgbiRy6tAtozAZwXLF5NzG9XBU16ou")
msg := message.NewCancel(from, 1000000, 1)
```

### 创建投票
```
from := arry.StringToAddress("xCJVPCgbiRy6tAtozAZwXLF5NzG9XBU16ou")
to := arry.StringToAddress("xC6nGfqHPt4KPoyhwCG3zNemNweYsBWXRR2")
msg := message.NewVote(from, to, 1000000, 1)
```

### 消息签名
```
msg.SignMsg(private)
```

### 发送消息

```
rpcMsg := types.MsgToRpcMsg(msg)
jsonBytes, _ := json.Marshal(rpcMsg)
req := &rpc.Request{Params: jsonBytes}
ctx, _ := context.WithTimeout(context.TODO(), time.Second*20)
resp, err := rpcClient.SendMessageRaw(ctx, req)
```
