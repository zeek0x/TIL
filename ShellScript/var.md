# 変数

このページはbashの仕様に基づいて記述する。

Bashには環境変数とシェル変数が存在する。

## シェル変数

`=`を使用してシェル変数に値を格納できる。

```console
$ n="XYZ"
$ echo $n
XYZ
```

シェル変数は子プロセスから参照できない。

```console
$ n="XYZ" | bash -c 'echo $n'

```

### よくある間違い

以下の例では、変数の中身の出力が得られるために一見値を取得できてるように見える。

```console
$ n="XYZ"; (echo $n)
XYZ
```

しかし、上の式は`echo $n`の変数`n`が展開され`echo XYZ`が実行されているのでサブシェルから変数を参照しているわけではない。

## 環境変数

`export`コマンドを使用して環境変数に値を格納できる。

```console
$ export n="XYZ"
$ echo $n
XYZ
```

環境変数は親プロセスから子プロセスに引き継ぐことができる。

```console
$ export n="XYZ" | bash -c 'echo $n'
XYZ
```

# 参考

- [BASH](https://linuxjm.osdn.jp/html/GNU_bash/man1/bash.1.html)
- [シェル変数と環境変数の違いをコマンドラインで確認する](https://qiita.com/kure/items/f76d8242b97280a247a1)
