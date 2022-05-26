# uniq コマンド

ソートされたファイルから内容の重なった行を削除する  

|オプション|説明|
|---|---|
|`-u, --unique`|一度だけ現われる行を出力|
|`-d, --repeated`|二度以上現れる行を出力|
|`-c, --count`|各行を出現回数と共に表示|
|`-number, -f, --skip-fields=number`|先頭から`number`フィールド分比較の対象から除外|
|`+number, -s, --skip-chars=number`|先頭から`number`文字分比較の対象から除外|
|`-w, --check-chars=number`|先頭から`number`文字分だけで比較|
|`--help`|使い方に関するメッセージを標準出力に表示|
|`--version`|バージョン情報を標準出力に表示|


## イディオム

月でまとめて最終日を取得する。

```
$ seq 90 -1 0 | xargs -I@ date '+%F' -d '2022-01-01 @day'
2022-03-31
2022-03-30
2022-03-29
...
2022-01-03
2022-01-02
2022-01-01
$ seq 89 -1 0 | xargs -I@ date '+%F' -d '2022-01-01 @day' | uniq -w7
2022-03-31
2022-02-28
2022-01-31
```

# 参考

- [Man page of UNIQ](https://linuxjm.osdn.jp/html/GNU_textutils/man1/uniq.1.html)
