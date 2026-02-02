[Index](./index.md) [Prev](./4006-debug.md) [Next](./4008-debug.md)

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
(gdb) break 2

Breakpoint 1 at 0x1131: file main.c, line 2.
```

----

From [GDB Docs/Linespec-Locations](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Linespec-Locations.html#Linespec-Locations)

```
<linenum>

    Specifies the line number <linenum> of the current source file.
```

----

```
Note: <linenum> is a <linespec> is a <locspec> used in: break <locspec>
```
