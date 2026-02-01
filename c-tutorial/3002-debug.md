[Index](./index.md) [Prev](./3001-debug.md) [Next](./3003-debug.md)

----

```c
/// main.c

#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main(void) {
  srand(time(NULL));
  int a = rand() % 11;
  int b = rand() % 11;
  int c = a + b;
  return c;
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
