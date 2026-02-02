[Index](./index.md) [Prev](./4017-debug.md) [Next](./4019-debug.md)

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
(gdb) return 99

#0  0x000055555555517a in main () at main.c:15
15		int n = b();
```

----

From [GDB Docs/Returning](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Returning.html#index-returning-from-a-function)

```
return
return expression

    You can cancel execution of a function call with the return command.

    If you give an expression argument, its value is used as the function’s return value. 
```
