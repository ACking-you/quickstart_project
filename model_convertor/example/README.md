## model_convertor example
不提供tag操作支持，只有config进行配置。
```go
	// 生成默认配置
t := model_convertor.DefaultConfig("root", "123", "127.0.0.1", 3306, "my_chat")
	// 开始修改默认配置
t.EnableJsonTag(true).
    // 生成struct的包名(默认为空的话, 则取名为: package model)
PackageName("models").
		// 是否添加结构体方法获取表名
RealTableNameMethod("TableName").
		// 生成的结构体保存路径
SavePath("./example/models/").
		// 只生成指定的表
Table("users").
		// 通过回调过滤不需要生成的表
TableFilterHook(func(s string) bool {
    if strings.Contains(s, "test") {
        return true
    }
    return false
})
```