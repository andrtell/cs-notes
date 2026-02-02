[Index](./index.md) [Prev](./4011-debug.md) [Next](./4013-debug.md)

----

```c
// main.c

int main(void) {
  return 0;
}
```

```sh
# compile
cc -O0 -g -o main main.c

# debug
gdb ./main
```

----

```
(gdb) break main

Breakpoint 1 at 0x1131: file main.c, line 4.

(gdb) delete 1
```

----

From [GDB Docs/Delete-Breaks](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Delete-Breaks.html#Delete-Breaks)

```
delete [breakpoints] [list…]

    Delete the breakpoints, watchpoints, tracepoints, or catchpoints
    of the breakpoint list specified as argument.

    If no argument is specified, delete all breakpoints, watchpoints,
    tracepoints, and catchpoints.
```
