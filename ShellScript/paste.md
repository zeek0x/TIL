# paste コマンド

ファイルを行単位で連結する。

- `-d` でデリミタを設定する（デフォルトはスペース）
- `-s` でファイル単位で１行にまとめる
- `-` で標準入力を入力として扱う

```console
$ echo -e "yummy\nyummy\nnot bad\namazing" | paste -d ',' fruits.txt price.txt -
apple,100,yummy
banana,200,yummy
orange,300,not bad
peach,,amazing
```

```console
$ cat tableinfo.txt
id INT
user_id VARCHAR(5)
user_name VARCHAR(10)
mail_address VARCHAR(20) CHECK (mail_address LIKE '%@%')
$ f=tableinfo.txt; paste -s <(cut -d ' ' $f -f 1) <(cut -d ' ' $f -f 2)
id	user_id	user_name	mail_address
INT	VARCHAR(5)	VARCHAR(10)	VARCHAR(20)
```

使用データ：[tableinfo.txt](https://github.com/shellgei/shellgei160/blob/master/qdata/141/tableinfo.txt)

# 参考

- [Man page of PASTE](https://linuxjm.osdn.jp/html/gnumaniak/man1/paste.1.html)
