[Index](./index.md) [Prev](./4002-debug.md) [Next](./4004-debug.md)

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

Breakpoint 1 at 0x1131: file main.c, line 2.
```

----

From [GDB Docs/Linespec-Locations](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Linespec-Locations.html#Linespec-Locations)

```
<linenum> is <linespec> is <locspec>
```

```
<linenum>

    Specifies the line number <linenum> of the current source file.

    example: (gdb) break 2

[...]

<filename>:<linenum>

    Specifies the line <linenum> in the source file <filename>.

    example: (gdb) break main.c:2

[...]

<function>

    Specifies the line that begins the body of the function <function>.

    example: (gdb) break main

[...]

<filename>:<function>

    Specifies the line that begins the body of the function <function> in the file <filename>.

    example: (gdb) break main.c:main

```
