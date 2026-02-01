[Index](./index.md) [Prev](./3001-debug.md) [Next](./3003-debug.md)

----

```c
int main() {
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

```
(gdb) run

[Inferior 1 (process 78037) exited normally]
```
