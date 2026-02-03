[Index](./index.md) [Prev](./4005-debug.md) [Next](./4007-debug.md)

----

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

```sh
# compile
cc -O0 -g -o main main.c

# debug
gdb ./main
```

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

----

[5.1.2 Setting Watchpoints](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Set-Watchpoints.html#Set-Watchpoints)
