# seq コマンド

`seq`コマンドは、数列を標準出力に表示する。このコマンドは、GNU Coreutilsに含まれる。

```bash
seq [option] [first [increment]] last
```

seq コマンドは`first`（デフォルト：`1`）から`last`までの数を`increment`（デフォルト：`1`）おきに表示する。

|オプション|ロングオプション|意味|
|--|--|--|
|`-f format`|`--format=format`|すべての数をformatを使用して表示する|
|`-s string`|`--separator=string`|数の区切りに`string`（デフォルト：改行）を使う|
|`-w`|`--equal-width`|すべての数を同じ桁数で表示する。先頭の空きは0で埋める|

# 参考

- [26.3 seq: 数列を表示する](https://linuxjm.osdn.jp/info/GNU_coreutils/coreutils-ja_185.html)
