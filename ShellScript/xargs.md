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

## 参考

- [【 xargs 】コマンド――コマンドラインを作成して実行する](https://atmarkit.itmedia.co.jp/ait/articles/1801/19/news014.html)
- [【Linux】xargs コマンドの使い方がよく分からない](https://techblog.kyamanak.com/entry/2018/02/12/202256)
