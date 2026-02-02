[Index](./index.md) [Prev](./4010-debug.md) [Next](./4012-debug.md)

----

```c
// main.c

int main(void) {
  int sum = 0;

  for (int n = 1; n <= 10; n++) {
    sum += n;
  }

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

```gdb
(gdb) rbreak ^main

Breakpoint 1 at 0x1131: file main.c, line 4.
```

----

From [GDB Docs/Set-Breaks](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Set-Breaks.html#Set-Breaks)

```
rbreak <regex>

    Set breakpoints on all functions matching the regular expression <regex>.
```
