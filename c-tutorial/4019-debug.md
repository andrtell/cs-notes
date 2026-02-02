[Index](./index.md) [Prev](./4017-debug.md) [Next](./4020-debug.md)

----

```c
// main.c

int a() {
	int v = 1
	return v;
}

int b() {
	int p = a();
	int q = p + 1;
	return q;
}

int main() {
	int n = b(); 
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

```gdb
(gdb) start

Temporary breakpoint 1, main () at main.c:15
15		int n = b();
```

```gdb
(gdb) next

16		return 0;
```

----

From [GDB Docs/Continuing-and-Stepping](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Continuing-and-Stepping.html#Continuing-and-Stepping)

```
next [count]

    Continue to the next source line in the current (innermost) stack frame.
    This is similar to step, but function calls that appear within the line
    of code are executed without stopping.
```
