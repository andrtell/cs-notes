[Index](./index.md) [Prev](./4000-debug.md) [Next](./4001-debug.md)

----

```c
// main.c

int main(void) {
  return 0;
}
```

----

```sh
# compile
cc -O0 -g -o main main.c

# debug
gdb ./main
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
Temporary breakpoint 1, main () at main.c:4
4		return 0;
```

_Arguments (works with both run and start)_

```

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
