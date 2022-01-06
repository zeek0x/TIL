# xargs コマンド

```
     +--stdin--+
     |         |
     |         v  |--Run command--|
$ commnad1 | xargs command2
               |              ^
               |              |
               +----stdout----+
```

前のコマンド(command1)のを標準入力を、`xargs`の引数のコマンド(command2)の引数としてそのコマンドを実行する。
`-p`オプションでどのようなコマンドラインとなるかを確認しながら実行することができる。

```console
$ echo {a..g}.txt | xargs -p rm
rm a.txt b.txt c.txt d.txt e.txt f.txt g.txt?...
```

また、コマンドを省略した場合には`echo`コマンドが使用される。

```console
$ echo {a..g}.txt | xargs -p
/bin/echo a.txt b.txt c.txt d.txt e.txt f.txt g.txt?...y
a.txt b.txt c.txt d.txt e.txt f.txt g.txt
```

## `-n`オプション

`-n数字`と指定すると、入力された文字列を指定された数字の数だけずつコマンドの引数に渡す。

```console
$ seq 5 | xargs -n3 echo
1 2 3
4 5
```

## `-I`オプション

`-I変数名`と指定すると、`xargs`コマンドの引数の文字列の中で変数を展開することができる。

```console
$ echo Medium | xargs -I@ echo 'Small @ Large'
```

## 参考

- [【 xargs 】コマンド――コマンドラインを作成して実行する](https://atmarkit.itmedia.co.jp/ait/articles/1801/19/news014.html)
- [【Linux】xargs コマンドの使い方がよく分からない](https://techblog.kyamanak.com/entry/2018/02/12/202256)
- [1日1問、半年以内に習得 シェル・ワンライナー160本ノック](https://gihyo.jp/book/2021/978-4-297-12267-6)
