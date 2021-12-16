# shebang

shebangとはShellScriptとして記述されたファイルの先頭に`#!ShellScriptコマンドへの絶対パス`の形式で記述するコメントのことである。shebangを記述することでそのファイルを実行する際のコマンドを指定することができる。

```console
bash-3.2$ cat <<EOF > a
> #!/bin/bash
>
> echo $0
> EOF
bash-3.2$ chmod +x a
bash-3.2$ ./a
bash
bash-3.2$ sh ./a
bash
bash-3.2$ sh
sh-3.2$ ./a
bash
```
