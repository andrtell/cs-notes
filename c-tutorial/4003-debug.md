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

Breakpoint 1 at 0x1131: file main2.c, line 2.
```

```gdb
(gdb) run

Breakpoint 1, main () at main2.c:2
2		return 0;
```

----

From [GDB Docs/Set-Breaks](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Set-Breaks.html#Set-Breaks)

```
break <locspec>

    Set a breakpoint at all the code locations in your program
    that result from resolving the given <locspec>
```

From [GDB Docs/Linespec-Locations](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Linespec-Locations.html#Linespec-Locations)

(modified excerpt)

```
<linenum>

    Specifies the line number <linenum> of the current source file.

    example: (gdb) break 2

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
