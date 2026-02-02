[Index](./index.md) [Prev](./4001-debug.md) [Next](./4003-debug.md)

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
(gdb) run

[Inferior 1 (process 130610) exited normally]
```

----

From [GDB Docs/Starting](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Starting.html#Starting)

```
run
r

Use the run command to start your program under GDB. [...]
```

