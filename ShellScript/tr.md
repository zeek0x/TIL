# tr コマンド

`tr`コマンドは、文字を変換・消去する。

## 文字の変換

第一引数の文字集合を第二引数の文字集合に変換する。

```console
$ echo abcdef | tr abc xyz
xyzdef
$ $ echo {a..z} | tr a-z A-Z
A B C D E F G H I J K L M N O P Q R S T U V W X Y Z
```

## 文字の消去

`-d`, `--delete` オプションで指定した文字集合を消去できる。

```console
$ echo abcdef | tr -d b-e
af
```

## 文字集合の指定

文字列を直接指定する以外に以下の指定方法がある。

|指定方法|指定例|例の対象|
|---|---|---|
|エスケープ文字|`\\`|`\`|
|範囲指定|`a-c`|`abc`|
|繰り返し文字|`[y*3]`|`yyy`|
|文字クラス|`alnum`|`abc..xyz123..789`|

# 参考

- ![Man page of TR](https://linuxjm.osdn.jp/html/GNU_textutils/man1/tr.1.html)
