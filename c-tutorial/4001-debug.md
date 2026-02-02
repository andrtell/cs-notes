[Index](./index.md) [Prev](./4001-debug.md) [Next](./4002-debug.md)

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

gdb -se ./main
```

----

```gdb
(gdb) start

Temporary breakpoint 1, main () at main2.c:2
2		return 0;
```
