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

----

```sh
# compile
cc -O0 -g -o main main.c

# debug
VAR=ABC gdb ./main
```

----

__run__

```
(gdb) run
[Inferior 1 (process 130610) exited normally]
```

__start__

```
(gdb) start
Temporary breakpoint 1, main (argc=1, argv=0x7fffffffde78) at main.c:5
5	  char *s = getenv("VAR");
```

__the _arguments_ (run & start)__

```
(gdb) start 1 $(pwd) $HOME
Temporary breakpoint 1, main (argc=4, argv=0x7fffffffde38) at main.c:4
4		return 0;

(gdb) show args
Argument list to give program being debugged when it is started is "1 $(pwd) $HOME".

(gdb) print argc
$1 = 4

(gdb) print *argv@argc
$2 = {0x7fffffffe1c0 "/tmp/main", 0x7fffffffe1ca "1", 0x7fffffffe1cc "/tmp", 0x7fffffffe1d1 "/home/bob"}
```

----

From [GDB Docs/Starting](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Starting.html#Starting)

```
run
r

    Use the run command to start your program under GDB.
```

```
start

    The ‘start’ command does the equivalent of setting a temporary breakpoint at
    the beginning of the main procedure and then invoking the ‘run’ command.
```

```
The arguments.

    Specify the arguments to give your program as the arguments of the run command.

    If a shell is available on your target, the shell is used to pass the arguments,
    so that you may use normal conventions (such as wildcard expansion or variable substitution)
    in describing the arguments. [...]
```
