# プロセス置換

このページはbashの仕様に基づいて記述する。

`>(command)`/`<(command)`の形式を指定するとこにより、`commnad`の標準入力/出力を展開先のコマンドへパイプすることができる。

`command`の標準入力/出力が`/dev/fd/$N`のファイルに接続される。このファイルの名前は、引数の形で展開され現在のコマンドに渡される。

標準入力として展開する。

```console
$ cat <(echo hoge)
hoge
```

プロセス置換は`/dev/fd/$N`の形式で展開されている。

```console
$ echo <(echo hoge)
/dev/fd/63
```

標準出力として展開する。

```console
$ echo hoge > >(cat)
```

標準入力の展開は複数コマンドの出力を受け取りたい時になどで役立つ。

```console
# command1 と command2 の標準出力を比較する
$ diff <(command1) <(command2)
# grep の結果を合わせて眺める
$ cat <(grep AAA log.txt) <(grep BBB log.txt) | sort
```

標準出力の展開はファイルにしか書き込めないコマンドなどで役立つ。

```console
# super_operate.sh は第一引数にログファイルへのパスを受け取る。
$ cat <<EOF > super_operate.sh
if [ \$# -lt 1 ]; then
    echo "usage: \$0 log_dir"
    exit 1
fi
echo "ok" > \$1
echo "Just write in log!"
EOF

# 実行するとログファイルへと ok が書き込まれている
$ bash super_operate.sh log.txt
Just write in log!
$ cat log.txt
ok

# 標準出力への展開によりcatへと書き込まれる内容が渡される。
# catはそれを標準出力へと出力する。
$ bash super_operate.sh >(cat)
Just write in log!
ok
# super_operate.sh側の標準出力を捨てると、cat側の内容のみ表示される。
$ bash super_operate.sh >(cat) > /dev/null
ok
```

# 参考

- [BASH](https://linuxjm.osdn.jp/html/GNU_bash/man1/bash.1.html)
- [bashのプロセス置換で遊んでみよう！](https://techblog.raccoon.ne.jp/archives/53726690.html)
