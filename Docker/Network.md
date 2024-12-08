# Docker ホストマシンのホスト名

Docker コンテナ内から Docker ホストマシンのホスト名は `host.docker.internal` で解決される（Docker for Desktop 限定）。

## 確認

- 以下のように、HTTPサーバをホストマシンで起動

```console
$ cat hello.txt 
Hello
$ python3 -m http.server --bind 0.0.0.0
Serving HTTP on 0.0.0.0 port 8000 (http://0.0.0.0:8000/) ...
```

- コンテナから `Curl` コマンドを実行し、先ほどの HTTP サーバにリクエストが送れることを確認する

```console
$ docker run --rm curlimages/curl --silent host.docker.internal:8000/hello.txt
Hello
```
