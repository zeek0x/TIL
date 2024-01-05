# パッケージへのパッチ

## 手動で取得

`go.mod` で `replace` を使用し、ディレクトリへのパスを上書きすることで `go get` で取得したパッケージができる。

```go.mod
require (
	golang.org/x/sys v0.16.0
)

replace (
	golang.org/x/sys => '../path/to/sys'
)
```

## go get で取得

`go get` で取得したパッケージに対して、一時的な修正を加えることができる。

まず `GOHOME` ディレクトリ内の対象のパッケージのファイルへ修正を加え、アプリケーションのプロジェクトで `go build -a` すればよい。
もし元に戻したいのであれば `go clean --modcache` を実行する。
