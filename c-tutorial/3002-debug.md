[Index](./index.md) [Prev](./3001-debug.md) [Next](./3003-debug.md)

----

```c
// main.c

int main(int argc, char *argv[]) {
  int status = 0;
  return status;
}
```

```sh
# compile

cc -O0 -g -o main main.c
```

```sh
# debug

gdb -se ./main
```

----

```gdb
(gdb) break main

Breakpoint 1 at 0x1138: file main.c, line 2.
```

```gdb
(gdb) run 1 $(pwd) $HOME

Breakpoint 1, main (argc=4, argv=0x7fffffffde48) at main.c:2
2		int status = 0;
```

```gdb
(gdb) show args

Argument list to give program being debugged when it is started is "1 $(pwd) $HOME".
```

```gdb
(gdb) print argc

$1 = 4
```

```gdb
(gdb) print *argv@argc

$2 = {0x7fffffffe1c0 "/tmp/main", 0x7fffffffe1ca "1", 0x7fffffffe1cc "/tmp", 0x7fffffffe1d1 "/home/bob"}
```

```gdb
(gdb) continue

[Inferior 1 (process 93334) exited normally]
```

```gdb
(gdb) quit
```

