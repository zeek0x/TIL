# 終了ステータス

終了ステータス（リターンコードともいう）

|終了ステータス|意味|
|---|---|
|0|正常終了|
|1|一般的なエラー|
|2|ビルトインコマンドの誤用または構文エラー|
|126|コマンドを実行できなかった|
|127|コマンドが見つからなかった|
|128|`exit`に不正な値を渡した|
|128+n|シグナルnで終了|
|255|範囲外の終了ステータス|

## パイプラインと終了ステータス

この項目はbashの仕様に基づいて記述する。

`?`パラメータ：最後に実行されたフォアグラウンドのパイプラインの終了ステータスが展開される。

```console
$ exit 2 | exit 1 | exit 0
$ echo $?
0
```

`PIPESTATUS`変数：フォアグラウンドで最後に実行したパイプラインの各プロセスの終了ステータスのリストとなるが展開される。

```console
$ exit 2 | exit 1 | exit 0
$ echo  ${PIPESTATUS[@]}
2 1 0
```

`pipefail`オプション：設定されている場合、パイプラインの実行含めスクリプト全体が中断される。中断された場合、中断されたコマンドの終了ステータスがパイプライン及びスクリプトの終了ステータスとなる。デフォルトは無効である。

```console
$ set -o pipefail # 有効化
$ set +o pipefail # 無効化
```

# 参考

- [Exit status](https://en.wikipedia.org/wiki/Exit_status)
- [終了ステータス](https://ja.wikipedia.org/wiki/%E7%B5%82%E4%BA%86%E3%82%B9%E3%83%86%E3%83%BC%E3%82%BF%E3%82%B9)
- [Appendix E. Exit Codes With Special Meanings](https://tldp.org/LDP/abs/html/exitcodes.html)
- [BASH](https://linuxjm.osdn.jp/html/GNU_bash/man1/bash.1.html)
