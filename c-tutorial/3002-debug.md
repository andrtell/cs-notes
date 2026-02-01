[Index](./index.md) [Prev](./3001-debug.md) [Next](./3003-debug.md)

----

```c
int main() {
  return 0;
}
```

```sh
# compile

cc -g -o main main.c
```

```sh
# debug

gdb ./main

(gdb) run

[Inferior 1 (process 78037) exited normally]
```
