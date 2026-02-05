[Index](./index.md) [Prev](./4004-debug.md) [Next](./4006-debug.md)

----

__Program__

```c
// main.c

int add(int a, int b) {
	int sum = a + b;
	return sum;
}

int times2(int c) {
	return add(c, c);
}

int main() {
	int val = 2;
	int res = times2(val);
	return 0;
}
```

_compile_

```sh
cc -O0 -g -o main main.c
```

_debug_

```sh
gdb ./main
```

__GDB__

_step_

```
(gdb) start

Temporary breakpoint 1, main () at main.c:13
13		int val = 2;

(gdb) step

14		int res = times2(val);

(gdb) step

times2 (c=2) at main.c:9
9		return add(c, c);

(gdb) step

add (a=2, b=2) at main.c:4
4		int sum = a + b;
```

_next_

```
(gdb) next

5		return sum;
```

_backtrace_

```
(gdb) backtrace

 #0  add (a=2, b=2) at main.c:4
 #1  0x0000555555555165 in times2 (c=2) at main.c:9
 #2  0x0000555555555184 in main () at main.c:14
```

_continue_

```
(gdb) continue

[Inferior 1 (process 153680) exited normally]
```

__Reference__

[5.2 Continuing and Stepping](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Continuing-and-Stepping.html#Continuing-and-Stepping)

[8.2 Backtraces](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Backtrace.html#Backtrace)
