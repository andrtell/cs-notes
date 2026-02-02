[Index](./index.md) [Prev](./4007-debug.md) [Next](./4009-debug.md)

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
(gdb) break main.c:2

Breakpoint 1 at 0x1131: file main.c, line 2.
```

----

From [GDB Docs/Linespec-Locations](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Linespec-Locations.html#Linespec-Locations)

```
<filename>:<linenum>

    Specifies the line <linenum> in the source file <filename>.
```

----

```
Note: <filename>:<linenum> is a <linespec> is a <locspec> used in: break <locspec>
```
