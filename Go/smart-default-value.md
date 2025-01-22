# スマートなデフォルト値の書き方

可変長引数を利用すると利用時の記述量が少ない。

- デフォルト値: `server.New()`
- カスタム値: `server.New(server.Config{x: 1})`

```go
package server

type Server struct {
    config: Config
}

type Config struct {
    x int
    y int
}

var defaultConfig = config{1, 2}

func New(config ...Config) *Server {
    cfg = defaultConfig
    if len(config) > 0 {
        cfg = config[0]
    }

    return &Server{config: cfg}
}
```
