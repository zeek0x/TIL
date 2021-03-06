# リダイレクト

## ファイル・ディスクリプター

|ファイル・ディスクリプター番号|出力先|
|---|---|
|0|標準入力|
|1|標準出力|
|2|標準エラー出力|
|n|任意の入出力先|

## リダイレクト

|演算子|名前|説明|
|---|---|---|
|`[n]<word`|入力のリダイレクト|入力をリダイレクトすると、wordを展開した結果の名前を持つファイルがオープンされ、ファイル・ディスクリプターnで読み込めるようになります。nが指定されていなければ、読み込みは標準入力(ファイル・ディスクリプター0)で行われます。|
|`[n]>word`|出力のリダイレクト|出力をリダイレクトすると、wordの展開した結果の名前を持つファイルがオープンされ、ファイル・ディスクリプターnで書き込めるようになります。nが指定されていなければ、書き込みは標準出力(ファイル・ディスクリプター1)に行われます。ファイルが存在しなかった場合は作成されます。ファイルが存在した場合はサイズ0に切り詰められます。|
|`[n]>>word`|リダイレクトによる追加出力|この形式を使って出力のリダイレクトを行うと、wordを展開した結果の名前を持つファイルがオープンされ、ファイル・ディスクリプターnに対する出力がこのファイルに追加されるようになります。nを指定しなければ、標準出力(ファイル・ディスクリプター1)で追加されます。ファイルが存在しなければ、新しく作られます。|
|`>&word`|標準出力と標準エラー出力のリダイレクト|この構造を使うと、標準出力(ファイル・ディスクリプター1)と標準エラー出力(ファイル・ディスクリプター2)の両方を、wordを展開した結果の名前を持つファイルにリダイレクトできます。|
|`&>>word`|標準出力と標準エラー出力の追加出力|この構造を使うと、標準出力(ファイル・ディスクリプター1)と標準エラー出力(ファイル・ディスクリプター2)の両方を、wordを展開した結果の名前を持つファイルに追加できます。|
|`[n]<&word`|入力ファイル・ディスクリプターの複製|入力ファイル・ディスクリプターを複製できます。wordが1桁以上の数値に展開された場合、nで示されるファイル・ディスクリプターが生成され、wordで指定された数値のファイル・ディスクリプターのコピーとなります。wordに含まれる数値が入力用にオープンされたファイル・ディスクリプターを指していない場合、リダイレクト・エラーが起きます。wordを評価した結果が-となった場合、ファイル・ディスクリプターnはクローズされます。nが指定されていない場合、標準入力(ファイル・ディスクリプター0)が使われます。|
|`[n]>&word`|出力ファイル・ディスクリプターの複製|出力ファイル・ディスクリプターを複製できます。nが指定されていない場合は、標準出力(ファイル・ディスクリプター1)が使われます。wordに含まれる数値が、出力用にオープンされたファイル・ディスクリプターを指していない場合、リダイレクト・エラーが起きます。特別な場合ですが、nが省略され、かつwordが1桁以上の数字には展開されなかった場合、前に説明したように標準出力と標準エラー出力がリダイレクトされます。|
|`[n]<&[digit]-`|出力ファイル・ディスクリプターの変更|ファイル・ディスクリプターのdigitをnに変更します。nが指定されていない場合は、標準入力 (ファイル・ディスクリプター 0) が使われます。digitはnに複製された後にクローズされます。digitが指定されていない場合は、単にnのファイル・ディスクリプターを閉じます。|
|`[n]>&[digit]-`|入力ファイル・ディスクリプターの変更|ファイル・ディスクリプターのdigitをnに変更します。nが指定されていない場合は、標準出力(ファイル・ディスクリプター 1)が使われます。digitが指定されていない場合は、単にnのファイル・ディスクリプターを閉じます。|
|`[n]<>word`|リダイレクト演算子|wordを展開した結果の名前を持つファイルがファイル・ディスクリプターnでの読み書きのためにオープンされます。nが指定されていなければ、ファイル・ディスクリプター0で読み書きが行われます。ファイルが存在しなければ、新しく生成されます。|

### ヒアドキュメント(Here Documents)

この形式のリダイレクトを用いると、シェルは現在のソースから入力を読み込みます。この読み込みはwordを単独で含む行(末尾にブランク文字があってはいけません)が現われるまで続きます。その行までに読み込んだ行は、コマンドの標準入力として扱われます。

ヒアドキュメントの形式を以下に示します:

```bash
<<[-]word
        here-document
delimiter
```

wordに対するパラメータ展開・コマンド置換・算術式展開・パス名展開は全く行われません。wordが一部でもクォートされている場合は、delimiterはwordのクォートをほどいた結果(クォート文字を削除した結果)となり、ヒアドキュメントに含まれる行では展開が行われなくなります。wordがクォートされていなければ、ヒアドキュメント中の全ての行に対してパラメータ展開・コマンド置換・算術式展開が行われます。wordがクォートされていない場合には、\\\<newline\>という文字列は無視され、\,$,`といった文字は\を用いてクォートしなければなりません。

リダイレクト演算子が<<-ならば、行頭にあるタブ文字は全て入力行およびdelimiterを含む行から取り除かれます。これにより、シェルスクリプト中のヒアドキュメントを自然な形でインデントさせることができます。

### ヒアストリング(Here Strings)

ヒアドキュメントの変形で、以下の形式です:

```
<<<word
```

wordは展開されてコマンドの標準入力に与えられます。

# 引用元

一部追記しています。

- [BASH](https://linuxjm.osdn.jp/html/GNU_bash/man1/bash.1.html)
