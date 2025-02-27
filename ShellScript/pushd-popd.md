# pushd, popd

ディレクトリを移動し、かつディレクトリ位置をスタックで管理できるシェルの組み込みコマンド

```console
$ pwd
/home/user
$ pushd tmp
/tmp ~
$ pwd
/tmp
$ pushd /usr/local
/usr/local /tmp ~
$ pwd
/usr/local
$ popd
/tmp ~
$ pwd
/tmp
$ popd
~
$ pwd
/home/user
$ popd
popd: directory stack empty
```
