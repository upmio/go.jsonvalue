# 快速上手

[上一页](./01_introduction.md) | [总目录](./README.md) | [下一页](03_get.md)

---

创建一个比如如下的复杂 JSON 对象：

```json
{
	"someObject": {
		"someObject": {
			"someObject": {
				"message": "Hello, JSON!"
			}
		}
	}
}
```

使用 jsonvalue 只需要三行:

```go
	v := jsonvalue.NewObject()
	v.SetString("Hello, JSON").At("someObject", "someObject", "someObject", "message")
	fmt.Println(v.MustMarshalString())
```

输出结果为: `{"someObject":{"someObject":{"someObject":{"message":"Hello, JSON!"}}}`

反过来，我们如果要直接读取上面的 json 数据，也可以这么用 jsonvalue: 

```go
const raw = `{"someObject": {"someObject": {"someObject": {"message": "Hello, JSON!"}}}}`
s := jsonvalue.MustUnmarshalString(s).GetString("someObject", "someObject", "someObject", "message")
fmt.Println(s)
```

输出结果为: `Hello, JSON!`


