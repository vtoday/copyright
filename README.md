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

### 请求 `查询版权交易平台账号信息` 接口

```go
    var res map[string]interface{}
    if e := client.DoRequestAndVerify("user.info", map[string]interface{}{"phone": "xxxxxx"}, &res); e != nil {
        //todo error
    }
    fmt.Println(res)
```

### 回调通知验签和数据解密

```go

    req *http.Request := ... //TODO 获取请求request
    request, err := copyright.ParseRequest(req)
    if err != nil {
        return
    }

    //校验请求
    if ok, e := client.VerifyRequestSign(request); !ok {
        return
    }

    //解密请求data
    data, e := client.DecryptRequestData(request)

    var param map[string]interface{}
    if err := json.Unmarshal([]byte(data), &param); err != nil {
        return
    }

    // do something ......

```
