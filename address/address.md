# 地址生成 文档
## 目录

### 工具包
```
github.com/Futuremine-chain/futuremine/common/param
github.com/Futuremine-chain/futuremine/futuremine/common/kit
github.com/Futuremine-chain/futuremine/tools/arry
```


###  生成BIP39助记词 

```
e, _ := kit.Entropy()
m, _ := kit.Mnemonic(e)
```

### 生成secp256k1私钥

```
key, _ := kit.MnemonicToEc(m)
```

###  生成地址

```
addr, _ := kit.GenerateAddress(param.MainNet, key.PubKey())
```

### 校验地址
```
kit.CheckAddress(param.MainNet, arry.StringToAddress("xC9MJyXesGsyXXVfLZuq2SNXarEuGUqnaGz"))
```

### 生成token地址

```
kit.GenerateTokenAddress(param.MainNet, arry.StringToAddress("xC9MJyXesGsyXXVfLZuq2SNXarEuGUqnaGz"), "HFC")
```

### 校验token地址

```
kit.CheckTokenAddress(param.MainNet, arry.StringToAddress("TfXDqmBTrmDxzJPzu9t2pBUsLqgPvo3WLZ2"))
```