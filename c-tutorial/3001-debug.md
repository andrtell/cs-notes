[Index](./index.md) [Prev](./2101-makefile.md) [Next](./3002-debug.md)

----

```c
int main() {
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
(gdb) run

[Inferior 1 (process 78037) exited normally]
```

```gdb
(gdb) break main

Breakpoint 1 at 0x1138: file main.c, line 2.
```

```gdb
(gdb) run

Breakpoint 1, main (argc=1, argv=0x7fffffffde38) at main.c:2
2		int status = 0;
```

```gdb
(gdb) next

3		return status;
```

```gdb
(gdb) continue

[Inferior 1 (process 91255) exited normally]
```

```gdb
(gdb) delete main
```

```gdb
(gdb) run

[Inferior 1 (process 92427) exited normally]
```

```gdb
(gdb) exit
```
