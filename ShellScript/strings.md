# strings コマンド

> strings - ファイル中の表示可能な文字列を表示する

```console
$ cat hello.c
#include <stdio.h>

int main(void)
{
	printf("Hello World!\n");
	return 0;
}
$ gcc hello.c; ./a.out
Hello World!
$ strings ./a.out | grep Hello
Hello World!
```

# 参考

- [Man page of strings]
