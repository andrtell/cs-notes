[Index](./index.md) [Prev](./2013-compilation.md) [Next](./3002-debug.md)

----

```c
/// main.c

#include <stdio.h>
#include <stdlib.h>

int main(void) {
  int a = rand() % 11;
  int b = rand() % 11;
  int c = a + b;
  printf("%d + %d = %d\n", a, b, c);
}
```

```sh
# compile

cc -g -o main main.c
```

```sh
# debug

gdb ./main

(gdb) exit
```

----

From https://sourceware.org/gdb/current/onlinedocs/gdb.html/Invocation.html#Invocation

```
type ‘gdb’ to start GDB.

type quit, exit or Ctrl-d to exit. 
```
