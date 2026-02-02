[Index](./index.md) [Prev](./4009-debug.md) [Next](./4011-debug.md)

----

```c
// main.c

int main(void) {
  int sum = 0;

  for (int n = 1; n <= 10; n++) {
    sum += n;
  }

  return 0;
}
```

```sh
# compile

cc -O0 -g -o main main.c
```

```sh
# debug

gdb ./main
```

----

```gdb
(gdb) break main

Breakpoint 1 at 0x1131: file main.c, line 4.
```

```gdb
(gdb) break 7

Breakpoint 2 at 0x1141: file main.c, line 7.
```

```gdb
(gdb) info break

Num     Type           Disp Enb Address            What
1       breakpoint     keep y   0x0000000000001131 in main at main.c:4
2       breakpoint     keep y   0x0000000000001141 in main at main.c:7
```

----

From [GDB Docs/Set-Breaks](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Set-Breaks.html#Set-Breaks)

```
info break [list…]

    Print a table of all breakpoints, watchpoints, tracepoints,
    and catchpoints set and not deleted. [...]
```
