[Index](./index.md) [Prev](./4000-debug.md) [Next](./4002-debug.md)

----

```c
// main.c

int main(void) {
  int sum = 0;
  for (int i = 1; i <= 5; i++) {
    sum += 1;
  }
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

__break__

```
(gdb) break main                                # other <locspec>:  main.c:main | 4 | main.c:4
Breakpoint 1 at 0x1131: file main.c, line 4.

(gdb) run
Breakpoint 1, main () at main.c:4
4		return 0;
```

__break .. if__

```
(gdb) break 6 if sum > 3
Breakpoint 2 at 0x1141: file main.c, line 6.

(gdb) continue
Breakpoint 2, main () at main.c:6
6	    sum += 1;

(gdb) info locals
i = 5
sum = 4
```

__info break__

```
(gdb) info break
Num     Type           Disp Enb Address            What
1       breakpoint     keep y   0x0000555555555131 in main at main.c:4
        breakpoint already hit 1 time
2       breakpoint     keep y   0x0000555555555141 in main at main.c:6
        stop only if sum > 3
        breakpoint already hit 1 time
```

----

From [GDB Docs/Set-Breaks](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Set-Breaks.html#Set-Breaks).


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

See [GDB Docs/Linespec-Locations](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Linespec-Locations.html#Linespec-Locations).
