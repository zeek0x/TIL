# paste コマンド

ファイルを行単位で連結する。

- `-d` でデリミタを設定する（デフォルトはスペース）
- `-` で標準入力を入力として扱う

```console
$ echo -e "yummy\nyummy\nnot bad\namazing" | paste -d ',' fruits.txt price.txt -
apple,100,yummy
banana,200,yummy
orange,300,not bad
peach,,amazing
```

# 参考

- [Man page of PASTE](https://linuxjm.osdn.jp/html/gnumaniak/man1/paste.1.html)
