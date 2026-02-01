[Index](./index.md) [Prev](./3004-debug.md) [Next](./3006-debug.md)

----

```c
// main.c

#include <stdio.h>

int main() {
    printf("Roses are red\n"
           "Violets are blue,\n"
           "Sugar is sweet\n"
           "And so are you.\n");
    return 0;
}
```

```sh
# compile

cc -O0 -g -o main main.c
```

```sh
# debug

gdb -se ./main
```

----

```gdb
(gdb) run > poem.txt

[Inferior 1 (process 111246) exited normally]
```

```gdb
(gdb) !cat poem.txt

Roses are red
Violets are blue,
Sugar is sweet
And so are you.
```
