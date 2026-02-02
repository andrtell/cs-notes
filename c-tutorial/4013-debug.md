[Index](./index.md) [Prev](./4012-debug.md) [Next](./4014-debug.md)

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
(gdb) clear main
```

----

From [GDB Docs/Delete-Breaks](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Delete-Breaks.html#Delete-Breaks)

```
clear <locspec>

    Delete any breakpoint with a code location that corresponds to <locspec>. 
```
