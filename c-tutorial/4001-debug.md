[Index](./index.md) [Prev](./4001-debug.md) [Next](./4002-debug.md)

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

```gdb
(gdb) list

1	int main(void) {
2		return 0;
3	}
```

----

