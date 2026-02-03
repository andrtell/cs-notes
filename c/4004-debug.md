[Index](./index.md) [Prev](./4003-debug.md) [Next](./4005-debug.md)

----

__Program__

```c
// main.c

int main(void) {
  return 0;
}
```

_compile_

```sh
cc -O0 -g -o main main.c
```

_debug_

```sh
gdb ./main
```

__GDB__

_clear_

```
(gdb) break main

(gdb) clear main
```

_delete_

```
(gdb) break main

Breakpoint 1 at 0x55555555515c: file main.c, line 4.

(gdb) delete 1
```

_enable / disable_

```
(gdb) break main

Breakpoint 1 at 0x55555555515c: file main.c, line 4.

(gdb) disable 1

(gdb) enable 1
```

__Reference__

[5.1.4 Deleting Breakpoints](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Delete-Breaks.html#Delete-Breaks)

[5.1.5 Disabling Breakpoints](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Disabling.html#Disabling)
