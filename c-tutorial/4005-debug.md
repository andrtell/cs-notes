[Index](./index.md) [Prev](./4004-debug.md) [Next](./4006-debug.md)

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

__step__

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

__next__

```
(gdb) next

 5		return sum;
```

__backtrace__

```
(gdb) backtrace

 #0  add (a=2, b=2) at main.c:4
 #1  0x0000555555555165 in times2 (c=2) at main.c:9
 #2  0x0000555555555184 in main () at main.c:14
```

__continue__

```
(gdb) continue

 [Inferior 1 (process 153680) exited normally]
```

----

From [GDB Docs/Continuing-and-Stepping](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Continuing-and-Stepping.html#Continuing-and-Stepping)

```
step

    Continue running your program until control reaches a different source line. [...]
```

```
next [count]

    Continue to the next source line in the current (innermost) stack frame.
    This is similar to step, but function calls that appear within the line
    of code are executed without stopping.
```

```
continue [ignore-count]
c        [ignore-count]
fg       [ignore-count]

    Resume program execution, at the address where your program last stopped. [...]
```


From [GDB Docs/Backtrace](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Backtrace.html#Backtrace)

```
backtrace [option]... [qualifier]... [count]
bt        [option]... [qualifier]... [count]

    Print the backtrace of the entire stack. [...]
```
