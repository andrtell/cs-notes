[Index](./index.md) [Prev](./4002-debug.md) [Next](./4004-debug.md)

----

```c
// main.c

int main(void) {
  int sum = 0;
  for (int n = 1; n <= 10; n++) {
    sum += n;
  }
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
(gdb) break 6 if sum > 40
Breakpoint 1 at 0x1141: file main.c, line 6.

(gdb) run
Breakpoint 1, main () at main.c:6
6	    sum += n;

(gdb) info locals
n = 10
sum = 45
```

----

From [GDB Docs/Set-Breaks](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Set-Breaks.html#Set-Breaks)

```
break ... if <cond>

    Set a breakpoint with condition <cond>;
    evaluate the expression cond each time the breakpoint is reached, and
    stop only if the value is nonzero—that is, if cond evaluates as true.
```
