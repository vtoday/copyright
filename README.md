# Copyright


### 安装

```shell
go get github.com/vtoday/copyright
```

### 客户端初始化

```go
    import (
        "github.com/vtoday/copyright"
    )

    privateKey := "MIIEvAIBADANBgkq......jkl9aD/5k8I/Hag=="
    publicKey := "MIIBIjANBgkq......IDAQAB"

    opens := []copyright.OptionFunc{}
    client, err := copyright.New("1001", privateKey, publicKey, false, opens...)
    if err != nil {
        return
    }
```
