# bc コマンド

## bc コマンドへの入力イディオム

標準入力（左側から）もしくはヒアドキュメント（右側から）で渡せる。

```console
$ echo '1+2+3' | bc
6
$ bc <<< '1+2+3'
6
```

## 基数変換

入力の基数を`ibase`, 出力の基数を`obase`で指定することができる。どちらもデフォルトでは10進数である。

```console
$ echo '10' | bc
10
$ echo 'ibase=16; 10' | bc
16
$ echo 'obase=16; 10' | bc
A
# obase の値は直前の ibase で指定した基数で評価される
$ echo 'ibase=16; obase=16; 10' | bc
 16
# ややこしいので ibase は最後に指定するとよい
$ echo 'obase=16; ibase=16; 10' | bc
10
```


# 参考

- [Man page of bc](https://linuxjm.osdn.jp/html/GNU_bc/man1/bc.1.html)
- [コマンドライン上で手軽に16進計算](https://qiita.com/tachesimazzoca/items/9c52aad0ff4d28b40324)
