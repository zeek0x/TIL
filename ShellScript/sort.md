# sort コマンド

テキストファイルをソートする。

## 動作モード

|オプション|説明|
|---|---|
|`-c`|ソート済みかのチェック|
|`-m`|まとめてソートとマージ|

## 出力順序

|オプション|説明|
|---|---|
|`-b`, `--ignore-leading-blanks`|行頭空白の無視|
|`-d`, `--dictionary-order`|辞書順でソート|
|`-f`, `--ignore-case`|大文字・小文字無視|
|`-i`, `--ignore-nonprinting`|印字可能でない文字を無視|
|`-M`|月の名称の省略形とみなしてソート|
|`-h`, `--human-numeric-sort`|人間が読むことができる形式でソート（例: 2K 1G)|
|`-n`, `--numeric-sort`|数値文字列として比較|
|`-R`, `--random-sort`|シャッフル|
|`-r`, `--reverse`|逆順にソート|


## その他

|オプション|説明|
|---|---|
|`-k POS1[,POS2]`|行の`POS1`から`POS2`（含む）までのフィールドでソートする|
|`-o OUTFILE`|出力先を標準出力から`OUTFILE`に変更する|
|`-t SEPARATOR`|ソートキーを検索する際、文字`SEPARATOR`をフィールドのセパレーターにする。デフォルトは空白|
|`-u`|重複を排除して出力する。`-c`オプション指定時には重複がないか検査する|
|`-z`|行の末尾が改行文字でなく、NUL文字として扱う|

## `-k` オプション

- 第３フィールドから末尾までをキーにする。

```console
sort -k3
```

- 第３フィールドのみをキーにする。

```console
sort -k3,3
```

- 第３フィールドのみをキーにし、数値として比較する。

```console
sort -k3,3n
```

`-k 3n,3`, `-k 3n,3n`　と指定しても等価である。

# 引用元

- [Man page of SORT](https://linuxjm.osdn.jp/html/gnumaniak/man1/sort.1.html)
- [sort(1) - Linux manual page](https://man7.org/linux/man-pages/man1/sort.1.html)
