# IFS(Internal Field Separator)

> 内部フィールド区切り文字です。展開を行った後に単語を分割する場合や、組み込みコマンドのreadを使ったときに行を単語に分割する場合に使われます。デフォルト値は<空白><タブ><改行>です。

## イディオム

|処理|記述|
|---|---|
|現在のIFSを確認|`printf "%q\n" "$IFS"`|
|スペース区切りで変数に設定|`echo A B C \| read a b c`|
|カンマ区切りで変数に設定|`IFS=','; echo A,B,C \| (read a b c; echo $a $b $c)`|
|区切った文字列を配列変数に設定|`echo A,B,C \| read -a arr`|

# 引用元

- [BASH](https://linuxjm.osdn.jp/html/GNU_bash/man1/bash.1.html)
