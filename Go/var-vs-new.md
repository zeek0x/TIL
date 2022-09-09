# var v.s. new

`var` キーワードによる宣言をしたポインタ変数と `new` キーワードによる初期化をした変数は値が異なる。

```
package main

import "fmt"

type T struct{}

func main() {
	var x *T
	y := new(T)
	fmt.Println(x, y) // <nil> &{}
}
```

- `var` キーワードによる宣言をしたポインタ変数: `<nil>`
- `new` キーワードによる初期化をした変数: 初期値
