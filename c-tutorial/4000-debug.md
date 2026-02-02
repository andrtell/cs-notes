[Index](./index.md) [Prev](./4000-debug.md) [Next](./4001-debug.md)

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

__run__

```
(gdb) run
[Inferior 1 (process 130610) exited normally]
```

__break__

```
(gdb) break main                                # or: [ main.c:main | 4 | main.c:4 ] 
Breakpoint 1 at 0x1131: file main.c, line 4.

(gdb) run
Breakpoint 1, main () at main.c:4
4		return 0;
```

__info break__

```
(gdb) info break
Num     Type           Disp Enb Address            What
1       breakpoint     keep y   0x0000000000001131 in main at main.c:4
```

__start__

```
(gdb) start
Temporary breakpoint 1, main () at main.c:4
4		return 0;
```

__enable / disable__

```
(gdb) break main
Breakpoint 1 at 0x1131: file main.c, line 4.

(gdb) disable 1

(gdb) run
[Inferior 1 (process 130610) exited normally]

(gdb) enable 1

(gdb) run
Breakpoint 1, main () at main.c:4
4		return 0;
```

__delete__

```
(gdb) break main
Breakpoint 1 at 0x1131: file main.c, line 4.

(gdb) delete 1
```

__clear__

```
(gdb) break main
Breakpoint 1 at 0x1131: file main.c, line 4.

(gdb) clear main
```

----

From [GDB Docs/Starting](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Starting.html#Starting)

```
run
r

    Use the run command to start your program under GDB.
```

```
start

    The ‘start’ command does the equivalent of setting a temporary breakpoint at
    the beginning of the main procedure and then invoking the ‘run’ command.
```

From [GDB Docs/Set-Breaks](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Set-Breaks.html#Set-Breaks).
See [GDB Docs/Linespec-Locations](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Linespec-Locations.html#Linespec-Locations).

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

From [GDB Docs/Delete-Breaks](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Delete-Breaks.html#Delete-Breaks)

```
delete [breakpoints] [list…]

    Delete the breakpoints, watchpoints, tracepoints, or catchpoints
    of the breakpoint list specified as argument.

    If no argument is specified, delete all breakpoints, watchpoints,
    tracepoints, and catchpoints.
```

```
clear <locspec>

    Delete any breakpoint with a code location that corresponds to <locspec>. 
```
