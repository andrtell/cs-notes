[Index](./index.md) [Prev](./3002-debug.md) [Next](./3004-debug.md)

----

```c
// main.c

int main(int argc, char *argv[]) {
  return 0;
}
```

```sh
# compile

cc -g -o main main.c
```

```sh
# debug

gdb -se ./main
```

----

```
(gdb) break main

Breakpoint 1 at 0x1138: file main.c, line 2.
```

```
(gdb) run a b c

Breakpoint 1, main (argc=4, argv=0x7fffffffde28) at main-1.c:2
2		return 0;
```

```
(gdb) print argc

$1 = 4
```

```
(gdb) print *argv@argc

$2 = {0x7fffffffe1a1 "/tmp/main", 0x7fffffffe1ba "a", 0x7fffffffe1bc "b", 0x7fffffffe1be "c"}
```
