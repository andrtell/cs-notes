[Index](./index.md) [Prev](./2101-makefile.md) [Next](./4001-debug.md)

----

__Program__

```c
// main.c
#include <stdlib.h>

int main(int argc, char *argv[]) {
  char *s = getenv("VAR");
  return 0;
}
```

_compile_

```sh
cc -O0 -g -o main main.c
```

_debug_

```sh
VAR=ABC gdb ./main
```

__Cheat Sheet__

| GDB              | Description                     | Example           |Reference                                                                                                       |
| ---------------- | ------------------------------- | ----------------  | -------------------------------------------------------------------------------------------------------------- |
| run              | Start program.                  |                   | [4.2 Starting your Program](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Starting.html#Starting)     |
| run [args]       |                                 | run $(pwd) $HOME  |                                                                                                                |
| start            | Start program. Break at main(). |                   |                                                                                                                |
| start [args]     |                                 |                   |                                                                                                                |
| break [locspec]  | Add breakpoint.                 | break main        | [5.1.1 Setting Breakpoints](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Set-Breaks.html#Set-Breaks) |
|                  |                                 | break main.c:main |                                                                                                                |
|                  |                                 | break main.c:5    |                                                                                                                |
|                  |                                 | break 5           |                                                                                                                |

__GDB__

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

__Reference__

[4.2 Starting your Program](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Starting.html#Starting)
