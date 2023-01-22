# alias と関数定義をサポートしていない

```console
$ cat .direnv
export XXX='xxx'
alias YYY='echo yyy'
$ direnv allow .
$ echo $XXX
xxx
$ YYY
zsh: command not found: YYY
```

- https://github.com/direnv/direnv/issues/73
