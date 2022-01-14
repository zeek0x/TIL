# 連想配列

このページはbashの仕様に基づいて記述する。

|処理|コマンド|
|---|----|
|空連想配列の生成|`declare -A arr=()`|
|連想配列の生成|`declare -A arr=([X]=1 [Y]=2)`|
|要素数の取得|`${#arr[@]}`|
|`k`の値を取得|`arr[$k]`|
|`k`の値を`v`に更新|`arr[$k]=$v`|
|`k`の値を削除|`unset arr[$n];`|
|値配列の取得|`${arr[@]}`|
|キー配列の取得|`${!arr[@]}`|

# 参考

- [BASH](https://linuxjm.osdn.jp/html/GNU_bash/man1/bash.1.html)
