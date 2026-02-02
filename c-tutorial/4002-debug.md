[Index](./index.md) [Prev](./4001-debug.md) [Next](./4003-debug.md)

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
(gdb) start
Temporary breakpoint 1, main () at main.c:4
4		return 0;
```

----

From [GDB Docs/Starting](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Starting.html#Starting)

```
start

    The ‘start’ command does the equivalent of setting a temporary breakpoint at
    the beginning of the main procedure and then invoking the ‘run’ command.
```

