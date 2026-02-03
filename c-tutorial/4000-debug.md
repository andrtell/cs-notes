[Index](./index.md) [Prev](./4000-debug.md) [Next](./4001-debug.md)

----

```c
// main.c
#include <stdlib.h>

int main(int argc, char *argv[]) {
  char *s = getenv("VAR");
  return 0;
}
```

```sh
# compile
cc -O0 -g -o main main.c

# debug
VAR=ABC gdb ./main
```

_run_

```
(gdb) run

[Inferior 1 (process 130610) exited normally]
```

_start_

```
(gdb) start

Temporary breakpoint 1, main (argc=1, argv=0x7fffffffde78) at main.c:5
5	  char *s = getenv("VAR");
```

_the arguments (run & start)_

```
(gdb) start 1 $(pwd) $HOME
```

```
(gdb) print argc

$1 = 4
```

```
(gdb) print *argv@argc

$2 = {0x7fffffffe1c0 "/tmp/main", 0x7fffffffe1ca "1", 0x7fffffffe1cc "/tmp", 0x7fffffffe1d1 "/home/bob"}
```

_the environment_

```
(gdb) show environment

VAR=ABC

(gdb) break main.c:6
```

```
(gdb) run
(gdb) info locals

s = 0x7fffffffec96 "ABC"
```

```
(gdb) set environment VAR=123
(gdb) run
(gdb) info locals

s = 0x7fffffffec96 "123"
```

----

[4.2 Starting your Program](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Starting.html#Starting)
