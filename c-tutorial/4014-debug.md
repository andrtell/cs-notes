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

# debug

gdb ./main
```

----

```
(gdb) break main

Breakpoint 1 at 0x1131: file main.c, line 4.
```

```
(gdb) disable 1

(gdb) enable 1
```

----

From [GDB Docs/Disabling](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Disabling.html#Disabling)

```
disable [breakpoints] [list…]

    Disable the specified breakpoints—or all breakpoints, if none are listed.
```

```
enable [breakpoints] [list…]

    Enable the specified breakpoints (or all defined breakpoints).
    They become effective once again in stopping your program.
```
