[Index](./index.md) [Prev](./4019-debug.md) [Next](./4021-debug.md)

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
(gdb) step 2

a () at main.c:4
4		int v = 1;
```

```gdb
(gdb) backtrace
#0  a () at main.c:4
#1  0x0000555555555153 in b () at main.c:9
#2  0x000055555555517a in main () at main.c:15
```

----

From [GDB Docs/Backtrace](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Backtrace.html#Backtrace)

```
backtrace [option]... [qualifier]... [count]
bt        [option]... [qualifier]... [count]

    Print the backtrace of the entire stack. [...]
```
