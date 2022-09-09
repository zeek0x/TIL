# ldd コマンド

> ldd - 共有ライブラリへの依存関係を表示する  

```console
$ cat hello.c
#include <stdio.h>

int main()
{
    printf("Hello World!\n");
}
$ gcc hello.c; ./a.out
Hello World!
$ ldd a.out
	linux-vdso.so.1 (0x0000ffff9acc1000)
	libc.so.6 => /lib/aarch64-linux-gnu/libc.so.6 (0x0000ffff9ab0c000)
	/lib/ld-linux-aarch64.so.1 (0x0000ffff9ac91000)
```

# 参考

- [Man page of LDD](https://linuxjm.osdn.jp/html/ld.so/man1/ldd.1.html)
