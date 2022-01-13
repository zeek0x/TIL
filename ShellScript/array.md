# 配列

このページはbashの仕様に基づいて記述する。

|処理|コマンド|
|---|----|
|空配列の生成|`arr=()`|
|配列の生成|`arr=(N M)`|
|要素数の取得|`${#arr[@]}`|
|先頭へ要素追加|`arr=(A "${arr[@]}")`|
|末尾へ要素追加|`arr=("${arr[@]}" Z)`|
|`n`番目の要素を取得|`${arr[$n]}`|
|`n`番目の要素を上書き|`arr[$n]=L`|
|`n`番目の要素を削除|`unset arr[$n];`|
|配列を詰め直す|`arr=("${arr[@]}")`|
|`n`番目から`m`個の部分配列を取得|`${arr[@]:$n:$m}`|

# 参考

- [BASH](https://linuxjm.osdn.jp/html/GNU_bash/man1/bash.1.html)
- [【bash】シェルの配列について](https://www.task-notes.com/entry/20150119/1421646435)
- [bash 配列まとめ](https://qiita.com/b4b4r07/items/e56a8e3471fb45df2f59)
