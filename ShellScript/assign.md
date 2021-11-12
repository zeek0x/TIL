# シェルスクリプトの代入

シェルスクリプト(bash/zsh)では、コマンドの prefix に`環境変数名=値`と指定することで、そのコマンドにおける環境変数の値を書き換えることができる。

```console
$ sh -c 'echo hoge is $HOGE .'
hoge is .
$ HOGE="Set All Right" sh -c 'echo hoge is $HOGE .'
hoge is Set All Right .
```

これは対象のコマンド内でだけ有効な一時的な代入となっている。実行しているシェル自体には反映されない。

```console
$ HOGE="Set All Right" echo hoge is $HOGE　# echo プログラムの内部でだけ有効であり、シェルからは見えない
hoge is
```

この場合はシェル変数に代入することで恒久的に値を参照できるようにする。

```console
$ HOGE="Set All Right"
$ echo hoge is $HOGE
hoge is Set All Right
```

ワンライナーで書きたい場合は、`;`（セミコロン）で区切りシェル変数へ代入する必要がある。シェル変数への代入となるので、その後も値を参照できてしまう点に注意する。

```console
$ unset HOGE
$ HOGE="Set All Right"; echo hoge is $HOGE
hoge is Set All Right
$ echo hoge is $HOGE
hoge is Set All Right
```

## 活用法

`LANG`環境変数を一時的に書き換えることで表示言語を変更する。

```console
$ date
2021年 11月12日 金曜日 11時42分23秒 JST
$ LANG=C date
Fri Nov 12 11:42:37 JST 2021
$ man bash        # 日本語版（古いことが多い）
$ LANG=C man bash # 英語版
```

## 参考

- [bashで環境変数をexportせずにシェルスクリプトを実行したい場合はコマンドの前に記述することで代替できる](https://shinkufencer.hateblo.jp/entry/2018/10/19/235900)
- [シェルスクリプトは変数代入で = の前後にスペースを置けない！･･･の本当の理由を知ると優れた文法が見えてくる](https://qiita.com/ko1nksm/items/9650ed1fc21d668f2732)
