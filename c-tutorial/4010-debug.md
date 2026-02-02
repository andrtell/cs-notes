[Index](./index.md) [Prev](./4009-debug.md) [Next](./4011-debug.md)

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

```gdb
(gdb) break main

(gdb) info break

Num     Type           Disp Enb Address            What
1       breakpoint     keep y   0x0000000000001131 in main at main.c:4
```

----

From [GDB Docs/Set-Breaks](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Set-Breaks.html#Set-Breaks)

```
info break [list…]

    Print a table of all breakpoints, watchpoints, tracepoints,
    and catchpoints set and not deleted. [...]
```
