[Index](./index.md) [Prev](./4002-debug.md) [Next](./4004-debug.md)

----

```c
// main.c

int main(void) {
  return 0;
}
```

----

```sh
# compile
cc -O0 -g -o main main.c

# debug
gdb ./main
```

----

```
(gdb) run

[Inferior 1 (process 130610) exited normally]

(gdb) break main                                # (or main.c:main or 4 or main.c:4)
Breakpoint 1 at 0x1131: file main.c, line 4.

(gdb) run
Breakpoint 1, main () at main.c:4
4		return 0;

(gdb) info break
Num     Type           Disp Enb Address            What
1       breakpoint     keep y   0x0000000000001131 in main at main.c:4
```

----

From [GDB Docs/Starting](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Starting.html#Starting)

```
run
r

    Use the run command to start your program under GDB.
```

From [GDB Docs/Set-Breaks](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Set-Breaks.html#Set-Breaks)
(Also see [GDB Docs/Linespec-Locations](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Linespec-Locations.html#Linespec-Locations))

```
break <locspec>

    Set a breakpoint at all the code locations in your program
    that result from resolving the given <locspec>.
```

```
info break [list…]

    Print a table of all breakpoints, watchpoints, tracepoints,
    and catchpoints set and not deleted.
```
