[Index](./index.md) [Prev](./4020-debug.md) [Next](./4022-debug.md)

----

```c
// main.c

int add(int a, int b) {
	int c = a + b
	return c;
}

int main() {
	int d = add(3, 7); 
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

Temporary breakpoint 1, main () at main.c:9
9		int d = add(3, 7);
```

```gdb
(gdb) step

add (a=3, b=7) at main.c:4
4		int c = a + b;
```

```gdb
(gdb) info args
a = 3
b = 7
```

```gdb
(gdb) next

5		return c;
```

```gdb
(gdb) info locals
c = 10
```

----

From [GDB Docs/Frame-Info](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Frame-Info.html#Frame-Info)

```
info args [-q]

    Print the arguments of the selected frame, each on a separate line.
```

```
info locals [-q]

    Print the local variables of the selected frame, each on a separate line.

    These are all variables (declared either static or automatic) accessible
    at the point of execution of the selected frame. 
```
