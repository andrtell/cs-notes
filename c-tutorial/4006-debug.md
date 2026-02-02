[Index](./index.md) [Prev](./4005-debug.md) [Next](./4007-debug.md)

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
(gdb) break main.c:main

Breakpoint 1 at 0x1131: file main.c, line 2.
```

----

From [GDB Docs/Linespec-Locations](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Linespec-Locations.html#Linespec-Locations)

```
<filename>:<function>

    Specifies the line that begins the body of the function <function> in the file <filename>.
```

----

```
Note: <filename>:<function> is a <linespec> is a <locspec> used in: break <locspec>
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
