# join コマンド

> 二つのファイルを読み、フィールドが共通な行を結合する  

二つのファイルを用意する。

```console
$ cat aaa.txt
001 apple
002 banana
003 orange
$ cat bbb.txt
001 2
001 3
002 1
004 1
```

`join FILE1 FILE2`で、`FILE1`、`FILE2`の共通な行について結合する。`-1 FIELD`オプション（デフォルト: 1）で指定された`FILE1`の`FIELD`番目のフィールドと`-2 FIELD`オプション（デフォルト: 1）で指定された`FILE2`の`FIELD`番目のフィールドを用いて結合が行われる。

```console
$ join aaa.txt bbb.txt
001 apple 2
001 apple 3
002 banana 1
```

`-a FILE-NUMBER`オプションを指定することで、`FILE-NUMBER`番目のファイルの行を全て表示することができる。

```console
$ join -a 1 aaa.txt bbb.txt
001 apple 2
001 apple 3
002 banana 1
003 orange
$ join -a 1 -a 2 aaa.txt bbb.txt
001 apple 2
001 apple 3
002 banana 1
003 orange
004 1
```

`awk`を利用してデフォルト値を設定する。

```console
$ join -a 1 aaa.txt bbb.txt | awk '!$3{$3=0}{print $0}'
001 apple 2
001 apple 3
002 banana 1
003 orange 0
```

# 参考

- [Man page of JOIN](https://linuxjm.osdn.jp/html/gnumaniak/man1/join.1.html)
