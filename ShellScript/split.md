# split コマンド

> split - ファイルを複数に分割する

第一引数のファイルを、第二引数の接頭辞を付加して採番したファイルに分割する。
第二引数のデフォルト値は`x`となる。

## オプション

|オプション|ロングオプション|意味|
|:---:|:---:|
|-b|--bytes=|指定したバイト毎に分割する|
|-d||接尾辞を 0 で始まる数字にする|
||--numeric-suffixes=|指定した番号を接尾辞の開始番号に設定できる|
|-n|--number=|指定した数にファイルを分割する|


## 例

1MB のファイルを 100KB ごとに分割する。

```console
$ du -h file
1.0M	file
$ split -b 100K file
$ du -h *
1.0M	file
100K	xaa
100K	xab
100K	xac
100K	xad
100K	xae
100K	xaf
100K	xag
100K	xah
100K	xai
100K	xaj
24K	xak
$ rm x*
```

接頭辞と接尾辞を設定する。

```console
$ split -b 100K --numeric-suffixes=1 file file.
$ du -h *
1.0M	file
100K	file.01
100K	file.02
100K	file.03
100K	file.04
100K	file.05
100K	file.06
100K	file.07
100K	file.08
100K	file.09
100K	file.10
24K	file.11
```

# 参考

- [Man page of SPLIT](https://linuxjm.osdn.jp/html/GNU_coreutils/man1/split.1.html)
