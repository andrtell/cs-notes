[Index](./index.md) [Prev](./4015-debug.md) [Next](./4017-debug.md)

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
(gdb) start

Temporary breakpoint 1, main () at main.c:4
4		int product = 1;

(gdb) continue

[Inferior 1 (process 148246) exited normally]
```

----

From [GDB Docs/Continuing-and-Stepping](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Continuing-and-Stepping.html#Continuing-and-Stepping)

```
continue [ignore-count]
c        [ignore-count]
fg       [ignore-count]

    Resume program execution, at the address where your program last stopped. [...]
```
