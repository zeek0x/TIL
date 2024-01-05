# Go のコマンド

- サブコマンド

|コマンド|例|説明|
|---|---|---|
|test|`go test ./...`|テストを実行する|
|install|`go install github.com/x-motemen/gore@latest`|ユーザのGo環境にパッケージをグローバルインストールする|
|get|`go get -u github.com/gin-gonic/gin`|プロジェクトの依存物にパッケージを追加する|
|vet|`go vet ./...`|バグの原因になりそうなコードを検出する|

- その他の公式ツール

|コマンド|例|説明|
|---|---|---|
|gofmt|`gofmt -w main.go`|Goのソースコードをフォーマットする|
|golint|`golint ./...`|Goらしくないコーディングスタイルに対して警告する|

- よく使う

| 用途 | コマンドライン | 
| --- | --- |
| カバレッジを出力する | `go test -cover ./... -coverprofile=cover.out` |
| カバレッジを可視化する | `go tool cover -html=cover.out -o cover.html` |
