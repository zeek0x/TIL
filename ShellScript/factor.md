# factor コマンド

`factor`コマンドは、素因数を表示する。このコマンドは、GNU Coreutilsに含まれる。

引数から受け取った値を素因数分解する。

```console
$ factor 57
57: 3 19
```

標準入力から受け取った値を素因数分解する。

```console
$ echo 1024 | factor
1024: 2 2 2 2 2 2 2 2 2 2
```

標準入力、引数両方を指定すると引数が優先される。

```console
$ echo 1024 | factor 57
57: 3 19
```

## 参考

- [26.1 factor: 素因数を表示する](https://linuxjm.osdn.jp/info/GNU_coreutils/coreutils-ja_180.html)
