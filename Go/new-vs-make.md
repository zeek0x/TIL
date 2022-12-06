# new v.s. make

- make(): スライス、マップ、チャンネル
- new(): その他のデータ型

```go
package main

import "fmt"

type T struct{}

func main() {
	var p *[]int = new([]int)    // allocates slice structure; *p == nil; rarely useful
	var v []int = make([]int, 5) // v now refers to a new array of 5 ints
	fmt.Println(p, v)            // &[] [0 0 0 0 0]
}
```


