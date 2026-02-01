[Index](./index.md) [Prev](./3002-debug.md) [Next](./3004-debug.md)

----

```c
// main.c

#include <stdlib.h>

int main() {
  char *s = getenv("X");
  return 0;
}
```

```sh
# compile

cc -O0 -g -o main main.c
```

```sh
# debug

X=A gdb -se ./main
```

----

```gdb
(gdb) break main.c:5

Breakpoint 1 at 0x1168: file main.c, line 5.
```

```gdb
(gdb) run

Breakpoint 1, main () at main.c:5
5		return 0;
```

```gdb
(gdb) print s

$1 = 0x7fffffffe3a0 "A"
```

```gdb
(gdb) show environment X

X = A
```

```gdb
(gdb) set environment X = C
```

```gdb
(gdb) run

Breakpoint 1, main () at main.c:5
5		return 0;
```

```gdb
(gdb) print s

$2 = 0x7fffffffe3a0 "C"
```
