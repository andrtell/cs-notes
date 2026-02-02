[Index](./index.md) [Prev](./4016-debug.md) [Next](./4018-debug.md)

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
(gdb) step

b () at main.c:9
9		int p = a();
```

```gdb
(gdb) step

a () at main.c:4
4		int v = 1;
```

----

From [GDB Docs/Continuing-and-Stepping](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Continuing-and-Stepping.html#Continuing-and-Stepping)

```
step

    Continue running your program until control reaches a different source line. [...]
```
