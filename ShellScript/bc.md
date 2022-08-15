# bc コマンド

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

標準入力もしくはファイル全体が一度に計算されるため基数変換の指定は一度でいい。

```console
$ echo -e '00\n01\n10\n11' | sed '1s/^/obase=10;ibase=2;\n/'
obase=10;ibase=2;
00
01
10
11
$ echo -e '00\n01\n10\n11' | sed '1s/^/obase=10;ibase=2;\n/' | bc
0
1
2
3
```

複数行で指定すると、1行目の `ibase=2` が２行目以降も有効なため、２行目以降の `obase=10` は出力を2進数にするという意味になってしまう。

```console
$ echo -e '00\n01\n10\n11' | sed 's/^/obase=10;ibase=2;/'
obase=10;ibase=2;00
obase=10;ibase=2;01
obase=10;ibase=2;10
obase=10;ibase=2;11
$ echo -e '00\n01\n10\n11' | sed 's/^/obase=10;ibase=2;/' | bc
0
1
10
11
```

## Tips

- 標準入力（左側から）もしくはヒアドキュメント（右側から）で渡せる。

```console
$ echo '1+2+3' | bc
6
$ bc <<< '1+2+3'
6
```


# 参考

- [Man page of bc](https://linuxjm.osdn.jp/html/GNU_bc/man1/bc.1.html)
- [コマンドライン上で手軽に16進計算](https://qiita.com/tachesimazzoca/items/9c52aad0ff4d28b40324)
