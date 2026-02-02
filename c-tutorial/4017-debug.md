[Index](./index.md) [Prev](./4016-debug.md) [Next](./4018-debug.md)

----

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

----

```sh
# compile
cc -O0 -g -o main main.c

# debug
gdb ./main
```

----

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

(gdb) backtrace
#0  add (a=2, b=2) at main.c:4
#1  0x0000555555555165 in times2 (c=2) at main.c:9
#2  0x0000555555555184 in main () at main.c:14
```

----

From [GDB Docs/Continuing-and-Stepping](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Continuing-and-Stepping.html#Continuing-and-Stepping)

```
step

    Continue running your program until control reaches a different source line. [...]
```

From [GDB Docs/Backtrace](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Backtrace.html#Backtrace)

```
backtrace [option]... [qualifier]... [count]
bt        [option]... [qualifier]... [count]

    Print the backtrace of the entire stack. [...]
```
