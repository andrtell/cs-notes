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
(gdb) run 1 2

Breakpoint 1, main (argc=3, argv=0x7fffffffde48) at main.c:2
2		int status = 0;
```

```gdb
(gdb) print argc

$1 = 3
```

```gdb
(gdb) print *argv@argc

$2 = {0x7fffffffe1c1 "/tmp/main", 0x7fffffffe1cb "1", 0x7fffffffe1cd "2"}
```

```gdb
(gdb) print status

$3 = 32767
```

```gdb
(gdb) next

3		return status;
```

```gdb
(gdb) print status

$4 = 0
```

```gdb
(gdb) continue

[Inferior 1 (process 93334) exited normally]
```

```gdb
(gdb) quit
```

