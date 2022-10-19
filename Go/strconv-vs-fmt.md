# strconv.Itoa v.s. fmt.Sprint

整数から文字列の変換において以下は等価。

```go
var x int
strconv.Itoa(x)
fmt.Sprint(x)
```

それぞれ引数が `strconv.Itoa` は `int` 、 `fmt.Sprint` は `any` なのでこの場面では `strconv.Itoa` を使った方がいい。
