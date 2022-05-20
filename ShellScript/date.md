# date コマンド

頻出するイディオムをまとめる。

引数にフォーマット、`-d`オプションで時刻指定を行う。

```console
# 現在時刻を表示
$ date
2022年  5月 1日 金曜日 01:23:45 UTC

# フォーマットを指定して表示
$ date '+%Y%m%d %H:%M:%S'
20220501 01:23:45

# Unixtimeフォーマット
$ date '+%s'
1651368225

# -d, --date オプションで表示する時間を指定可能
$ date -d '2020-07-07'
2020年  7月  7日 火曜日 00:00:00 UTC

# 相対時間指定
$ date -d '6 days ago'
2022年  4月 25日 月曜日 00:00:00 UTC

# 指定時刻から相対時間指定
$ date -d '6 days ago 2020-07-07'
2020年  7月  1日 水曜日 00:00:00 UTC

# Unixtime指定
$ date -d '@1651368225'
2022年  5月  1日 日曜日 01:23:45 UTC

# タイムゾーンを指定
$ TZ="Asia/Tokyo" date
2022年  5月  1日 日曜日 10:23:45 JST
```

# 参考

- [Man page of DATE](https://linuxjm.osdn.jp/html/GNU_coreutils/man1/date.1.html)
