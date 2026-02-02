[Index](./index.md) [Prev](./4013-debug.md) [Next](./4015-debug.md)

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
(gdb) disable 1
```

```gdb
(gbd) run

[Inferior 1 (process 144780) exited normally]
```

```gdb
(gdb) enable once 1
```

```gdb
(gdb) run

Breakpoint 1, main () at main.c:4
4		return 0;
```




----

From [GDB Docs/Disabling](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Disabling.html#Disabling)

```
disable [breakpoints] [list…]

    Disable the specified breakpoints—or all breakpoints, if none are listed.
```

From [GDB Docs/Disabling](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Disabling.html#Disabling)

```
enable [breakpoints] [list…]

    Enable the specified breakpoints (or all defined breakpoints).
    They become effective once again in stopping your program.
```

```
enable [breakpoints] once list…

    Enable the specified breakpoints temporarily.

    GDB disables any of these breakpoints immediately after stopping your program.
```

```
enable [breakpoints] count count list…

    Enable the specified breakpoints temporarily.

    GDB records count with each of the specified breakpoints,
    and decrements a breakpoint’s count when it is hit.

    When any count reaches 0, GDB disables that breakpoint.
```
