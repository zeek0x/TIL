# PCRE

## 先読みと後読み

|名前|パターン|例|
|---|---|---|
|肯定的先読み|`(?=pattern)`|`foo(?=bar)`|
|否定的先読み|`(?!pattern)`|`foo(?!bar)`|
|肯定的後読み|`(?<=pattern)`|`(?<=bar)foo`|
|否定的後読み|`(?<!pattern)`|`(?<!bar)foo`|

## キャプチャ

>CAPTURING
>
>         (...)           capture group
>         (?<name>...)    named capture group (Perl)
>         (?'name'...)    named capture group (Perl)
>         (?P<name>...)   named capture group (Python)
>         (?:...)         non-capture group
>         (?|...)         non-capture group; reset group numbers for
>                          capture groups in each alternative


## 後方参照(Backreference)

`(?<name>pattern)`という形式でキャプチャ内の正規表現でマッチした"値"を、後方から `\g{name}`という形式で指定できる。

```console
$ echo '123-123' | grep -P '(?<three_chars>...)-\g{three_chars}'
123-123
```

"値"としてマッチしているため、値が異なればマッチしなくなる。

```
$ echo '123-456' | grep -P '(?<three_chars>...)-\g{three_chars}'
```

キャプチャでは 1 から始まる連番で名前が割り当てられているため `?<name>`を省略した場合でも指定できる。また `\n` の形式でも指定できる。

```console
$ echo '123-123' | grep -P '(?<three_chars>...)-\g{1}'
123-123
$ echo '123-123' | grep -P '(...)-\g{1}'
123-123
$ echo '123-123' | grep -P '(...)-\1'
123-123
```

## 部分式呼び出し(subroutine call)

`(?<name>pattern)` という形式でキャプチャ内の正規表現を、別の箇所から `\g<name>` という形式で指定できる。

```console
$ echo '123-123' | grep -P '(?<three_chars>...)-\g<three_chars>'
123-123
```

後方参照とは異なり正規表現を再利用しているため、パターン間での値の関係はない。

```console
$ echo '123-456' | grep -P '(?<three_chars>...)-\g<three_chars>'
123-456
```

キャプチャの採番は共通なので、同様に数字で指定できる。また `(?n)` の形式でも指定できる。

```console
$ echo '123-456' | grep -P '(?<three_chars>...)-\g<1>'
123-456
$ echo '123-456' | grep -P '(...)-\g<1>'
123-456
$ echo '123-456' | grep -P '(...)-(?1)'
123-456
```

## 非キャプチャグループ

```console
$ echo abcabc | grep -P '(?:a)(?:b)(c)ab\1'
abcabc
```

## 対応する括弧

```console
$ echo '(1(2(3)4)5)(6)'| grep -P '\(((?>[^()]+)|(?R))*\)'
(1(2(3)4)5)(6)
```

# 参考

- [PCRE: Perl Compatible Regular Expressions](https://theriault.github.io/pcre-syntax/)
- [PCRE2 - Perl-compatible regular expressions (revised API)](https://www.pcre.org/pcre2.txt)
