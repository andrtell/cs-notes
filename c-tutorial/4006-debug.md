[Index](./index.md) [Prev](./4005-debug.md) [Next](./4007-debug.md)

----

__Program__

```c
// main.c

int main(void) {
	int product = 1;
	for (int n = 1; n <= 10; n++) {
		product *= n;
	}
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

_watch_

```
(gdb) start

Temporary breakpoint 1, main () at main.c:4
4		int product = 1;

(gdb) watch product

Hardware watchpoint 2: product

(gdb) continue

Hardware watchpoint 2: product

Old value = -8584
New value = 1
main () at main.c:5
5		 for (int n = 1; n <= 10; n++) {

(gdb) continue

Hardware watchpoint 2: product

Old value = 1
New value = 2
main () at main.c:5
5		 for (int n = 1; n <= 10; n++) {
```

__Reference__

[5.1.2 Setting Watchpoints](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Set-Watchpoints.html#Set-Watchpoints)
