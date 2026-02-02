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

```
(gdb) break main

Breakpoint 1 at 0x555555555131: file main.c, line 4.
```

```
(gdb) run

Breakpoint 1, main () at main.c:4
4		return 0;
```

----

From [GDB Docs/Set-Breaks](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Set-Breaks.html#Set-Breaks)

```
break <locspec>

    Set a breakpoint at all the code locations in your program
    that result from resolving the given <locspec>
```
