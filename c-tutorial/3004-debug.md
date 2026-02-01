[Index](./index.md) [Prev](./3003-debug.md) [Next](./3005-debug.md)

----

```c
// main.c

#include <stdlib.h>
#include <unistd.h>

int main() {
    char *s = getcwd(NULL, 0);
    free(s);
    return 0;
}
```

```sh
# compile

cc -O0 -g -o main main.c
```

```sh
# debug

env --chdir=/tmp gdb -se ./main
```

----

```gdb
(gdb) break main.c:6

Breakpoint 1 at 0x1188: file main.c, line 6.
```

```gdb
(gdb) run

Breakpoint 1, main () at main.c:6
6		free(s);
```

```gdb
(gdb) print s

$1 = 0x5555555592a0 "/tmp"
```

```gdb
(gdb) pwd

Working directory /tmp.
```

```gdb
(gdb) cd /home
```

```gdb
(gdb) run

Breakpoint 1, main () at main.c:6
6		free(s);
```

```gdb
(gdb) print s

$2 = 0x5555555592a0 "/home"
```
