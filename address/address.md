# 地址生成 文档
## 目录

### 工具包
```
github.com/Futuremine-chain/future/common/param
github.com/Futuremine-chain/future/future/common/kit
github.com/Futuremine-chain/future/tools/arry
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
addr, _ := kit.GenerateAddress(param.MainNet, "021c39e5bae2894676b8c70d8ba25f84ef70ac59440fcd585640bda8d02646d4b5")
```

### 校验地址
```
kit.CheckAddress(param.MainNet, "xC9MJyXesGsyXXVfLZuq2SNXarEuGUqnaGz")
```

### 生成token地址

```
kit.GenerateTokenAddress(param.MainNet, "xC9MJyXesGsyXXVfLZuq2SNXarEuGUqnaGz", "HFC")
```

### 校验token地址

```
kit.CheckTokenAddress(param.MainNet, "TfXDqmBTrmDxzJPzu9t2pBUsLqgPvo3WLZ2")
```