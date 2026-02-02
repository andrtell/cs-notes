[Index](./index.md) [Prev](./4008-debug.md) [Next](./4010-debug.md)

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
(gdb) break 7 if sum > 40

Breakpoint 1 at 0x1141: file main.c, line 7.
```

```gdb
(gdb) run

Breakpoint 1, main () at main.c:7
7			sum += n;
```

```gdb
(gdb) print sum

$1 = 45
```

----

