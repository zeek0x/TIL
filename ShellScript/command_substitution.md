# コマンド置換

このページはbashの仕様に基づいて記述する。

> コマンド置換(command substitution)を用いると、コマンド名をコマンドの出力で置き換えられます。コマンド置換には以下の2つの形式があります:
>
> `$(command)`
>
> または
>
> `\`command`\`
>
> bashはcommandを実行し、commandの標準出力でコマンド置換の部分を置き換えます。この際、末尾の改行文字は削除されます。文字列の途中にある改行文字は削除されませんが、単語分割の際に削除されることがあります。コマンド置換`$(cat file)`は、同じ意味を持ち、しかも高速な`$(< file)`に置き換え可能です。

# 引用元

- [BASH](https://linuxjm.osdn.jp/html/GNU_bash/man1/bash.1.html)