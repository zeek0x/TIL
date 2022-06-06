# sed コマンド

## 置換

```console
$ echo クロロエチルエチルエーテル | sed 's/エ/メ/'
クロロメチルエチルエーテル
```

`s`が文字の置換を意味しており、`sed 's/文字列1/文字列2/'`は「与えられた行の最初の文字列1を文字列2に置換する」を意味している。

```console
$ echo クロロエチルエチルエーテル | sed 's/エチルエ/エチルメ/'
クロロエチルメチルエーテル
```

検索文字列を長くして2度目の「エチル」の「エ」を「メ」に置換している。

```console
$ echo クロロエチルエチルエーテル | sed 's/エ/メ/g'
クロロメチルメチルメーテル
```

すべての検索対象文字列を置換したい場合は、`g`を付ける。

```console
$ echo クロロエチルエーテル | sed 's/エチル/&&/'
クロロエチルエチルエーテル
```

`&`を使用すると検索対象の文字を再利用することができる。

```console
$ echo クロロメチルエチルエーテル | sed -E 's/(メチル)(エチル)/\2\1/'
クロロエチルメチルエーテル
```

検索対象の文字列を括弧で囲むことで順番に番号が与えられ、置換後の文字列で`\1`, `\2`, ... と呼び出すことができる。このような文字列の再利用機能は後方参照と呼ばれる。`-E`オプションで拡張正規表現を有効化して、括弧にエスケープ文字を書かずに済むようにしている。

## 拡張正規表現

`-r`, `-E`, `--regex-extended` オプションを指定すると拡張正規表現(ERE: Extended Reuglar Exression)を使用する。


## 挿入

`{n}i{str}`の形式の`i`コマンドで`n`行目の前に、`{n}a{str}`の形式の`a`コマンドで`n`行目の後に`str`文字列の行を挿入できる。
全体の行数が`n`に満たない場合、挿入は無視される。

```console
$ echo -e 'AAA\nBBB\nCCC' | sed 2iXXX
AAA
XXX
BBB
CCC
$ echo -e 'AAA\nBBB\nCCC' | sed 2aXXX
AAA
BBB
XXX
CCC
$ echo 'AAA' | sed 2iXXX
AAA
$ echo 'AAA' | sed 2aXXX
AAA
```

範囲指定も可能である。

```console
$ echo -e 'AAA\nBBB\nCCC' | sed 2,3iXXX
AAA
XXX
BBB
XXX
CCC
$ echo -e 'AAA\nBBB\nCCC' | sed 2,3aXXX
AAA
BBB
XXX
CCC
XXX
```

## `-e`オプション

`sed`コマンドは位置引数を`sed script input-file`のように解釈する。
`-e`(`--expression`)オプションを指定することでスクリプトであることを明示できる。
複数指定した場合は前方から適用される。

```console
$ seq 3 | sed -e 's/[1-3]/4/' -e 's/4/5/'
5
5
5
```

## `-n`オプション

各行を出力しないように設定し、出力コマンド(`p`)が適用された行のみ出力する。

```console
$ seq 5 | sed -n '/[2-4]/p'
2
3
4
```

## `-z`オプション

行を跨いで文字列を検索する。

```console
$ echo -e 'うんち\nく' | sed -zE 's/うんち\nく/蘊蓄/'
蘊蓄
```

## 正規表現アドレス

正規表現アドレス`/regex/`を配置すると`regex`にマッチした行のみがスクリプトの対象となる。またアドレスとスクリプトの間に`!`を配置するとマッチしなかった行のみがスクリプトの対象となる。

```console
$ echo -e 'abc\ndef' | sed '/e/s/.*/xyz/'
abc
xyz
$ echo -e 'abc\ndef' | sed '/e/!s/.*/xyz/'
xyz
def
```


## 参考

- [1日1問、半年以内に習得 シェル・ワンライナー160本ノック](https://gihyo.jp/book/2021/978-4-297-12267-6)
- [Man page of SED](https://linuxjm.osdn.jp/html/GNU_sed/man1/sed.1.html)
