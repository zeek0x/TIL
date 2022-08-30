# Go のコマンド

- サブコマンド

|コマンド|例|説明|
|---|---|---|
|install|`go install github.com/x-motemen/gore@latest`|ユーザのGo環境にパッケージをグローバルインストールする|
|get|`go get -u github.com/gin-gonic/gin`|プロジェクトの依存物にパッケージを追加する|
|vet|`go vet ./...`|バグの原因になりそうなコードを検出する|

- その他の公式ツール

|コマンド|例|説明|
|---|---|---|
|gofmt|`gofmt -w main.go`|Goのソースコードをフォーマットする|
|golint|`golint ./...`|Goらしくないコーディングスタイルに対して警告する|
