[Index](./index.md) [Prev](./4004-debug.md) [Next](./4009-debug.md)

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

```
(gdb) break main
            main.c:main
            4
            main.c:4

Breakpoint 1 at 0x1131: file main.c, line 4.
```

----

See [GDB Docs/Linespec-Locations](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Linespec-Locations.html#Linespec-Locations)
