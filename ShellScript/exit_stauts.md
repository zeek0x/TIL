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

# 参考

- [Exit status](https://en.wikipedia.org/wiki/Exit_status)
- [終了ステータス](https://ja.wikipedia.org/wiki/%E7%B5%82%E4%BA%86%E3%82%B9%E3%83%86%E3%83%BC%E3%82%BF%E3%82%B9)
- [Appendix E. Exit Codes With Special Meanings](https://tldp.org/LDP/abs/html/exitcodes.html)
