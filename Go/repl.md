# REPL

Go　の REPL(Read-Eval-Print Loop) 環境を構築する。

```console
$ go install github.com/x-motemen/gore/cmd/gore@latest
$ go install github.com/k0kubun/pp@latest
```

- [x-motemen/gore](github.com/x-motemen/gore): Yet another Go REPL that works nicely. Featured with line editing, code completion, and more.
- [k0kubun/pp](github.com/k0kubun/pp): Colored pretty printer for Go language


```
$ gore -autoimport
gore version 0.5.5  :help for help
gore> 1+1
2
gore> fmt.Println("やっはろーワールド")
やっはろーワールド
28
nil
gore> 1+1
やっはろーワールド
2
```

`fmt.Println` 関数を実行するとその後の行の実行でも出力されるようになってしまう。
