# 変数展開

このページはbashの仕様に基づいて記述する。

|処理|表現|
|---|----|
|デフォルト値の使用|`${parameter:-word}`|
|デフォルト値の代入|`${parameter:=word}`|
|空文字列もしくは未設定時にエラーを表示|`${parameter:?word}`|
|代替値を使用|`${parameter:+word}`|
|デフォルト値の使用|`${parameter:-word}`|
|部分文字列展開|`${parameter:offset}`, `${parameter:offset:length}`|
|前方一致する変数名を展開|`${!prefix*}`, `${!prefix@}`
|配列のキーリスト|`${!name[@]}`, `${!name[*]}`|
|値の文字列長を取得|`${#parameter}`|
|前方一致したパターンの除去|`${parameter#word}`, `${parameter##word}`|
|後方一致したパターンの除去|`${parameter%word}`, `${parameter%%word}`|
|パターンの置換|`${parameter/pattern/string}`|
|大文字小文字の変換|`${parameter^pattern}`, `${parameter^^pattern}`, `${parameter,pattern}`, `${parameter,,pattern}`|

# 参考

- [BASH](https://linuxjm.osdn.jp/html/GNU_bash/man1/bash.1.html)
