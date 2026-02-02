[Index](./index.md) [Prev](./4003-debug.md) [Next](./4005-debug.md)

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

(gdb) next
5		return sum;

(gdb) continue
[Inferior 1 (process 153680) exited normally]
```

----

From [GDB Docs/Set-Breaks](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Set-Breaks.html#Set-Breaks)

```
break ... if <cond>

    Set a breakpoint with condition <cond>;
    evaluate the expression cond each time the breakpoint is reached, and
    stop only if the value is nonzero—that is, if cond evaluates as true.
```

From [GDB Docs/Frame-Info](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Frame-Info.html#Frame-Info)

```
info locals [-q]

    Print the local variables of the selected frame, each on a separate line.

	These are all variables (declared either static or automatic) accessible
	at the point of execution of the selected frame.
```
