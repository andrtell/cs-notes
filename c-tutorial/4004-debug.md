[Index](./index.md) [Prev](./4003-debug.md) [Next](./4005-debug.md)

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

__clear__

```
(gdb) break main
Breakpoint 1 at 0x1131: file main.c, line 4.

(gdb) clear main
```

__delete__

```
(gdb) break main
Breakpoint 1 at 0x1131: file main.c, line 4.

(gdb) delete 1
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

----

From [GDB Docs/Delete-Breaks](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Delete-Breaks.html#Delete-Breaks)

```
clear <locspec>

    Delete any breakpoint with a code location that corresponds to <locspec>. 
```

```
delete [breakpoints] [list…]

    Delete the breakpoints, watchpoints, tracepoints, or catchpoints
    of the breakpoint list specified as argument.

    If no argument is specified, delete all breakpoints, watchpoints,
    tracepoints, and catchpoints.
```

From [GDB Docs/Disabling](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Disabling.html#Disabling)

```
disable [breakpoints] [list…]
dis

    Disable the specified breakpoints—or all breakpoints, if none are listed.
    A disabled breakpoint has no effect but is not forgotten.

    All options such as ignore-counts, conditions and commands are remembered
    in case the breakpoint is enabled again later.

    You may abbreviate disable as dis.
```

```
enable [breakpoints] [list…]

    Enable the specified breakpoints (or all defined breakpoints).

    They become effective once again in stopping your program.
```

