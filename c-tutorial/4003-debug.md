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
(gdb) start

Temporary breakpoint 1, main () at main2.c:2
2		return 0;
```

----

From [GDB Docs/Starting](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Starting.html#Starting)

```
start

[...]

The ‘start’ command does the equivalent of setting a temporary breakpoint at
the beginning of the main procedure and then invoking the ‘run’ command.
```

