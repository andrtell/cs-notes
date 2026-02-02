[Index](./index.md) [Prev](./3007-debug.md) [Next](./3009-debug.md)

----

```c
// main.c

#include <stdio.h>

int sigma(int from, int to) {
	int sum = 0;
	for (int n = from; n <= to; n++) {
		sum += n;
	}
	return sum;
}

int main(void) {
  int from = 1;
  int to   = 10;
  int sum  = sigma(from, to);
  printf("The sum of all integers from %d to %d is %d\n", from, to, sum);
  return 0;
}
```

```sh
# compile

cc -O0 -g -o main main.c
```

```sh
# debug

gdb -se ./main
```

----

```gdb
(gdb) break 8 if sum > 37

Breakpoint 4 at 0x1166: file main.c, line 8.
```

```gdb
(gdb) run

Breakpoint 1, sigma (from=1, to=10) at main.c:8
8			sum += n;
```

```gdb
(gdb) p sum

$1 = 45
```

```gdb
(gdb) continue

The sum of all integers from 1 to 10 is 55

[Inferior 1 (process 126255) exited normally]
```

