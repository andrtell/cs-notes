[Index](./index.md) [Prev](./3006-debug.md) [Next](./3008-debug.md)

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
# run

./main

The sum of all integers from 1 to 10 is 55
```

```sh
# debug

gdb -se ./main
```

----

```gdb
(gdb) break 14

Breakpoint 1 at 0x1189: file main.c, line 14.
```

```gdb
(gdb) break main.c:18

Breakpoint 2 at 0x11a9: file main.c, line 18.
```

```gdb
(gdb) break sigma

Breakpoint 3 at 0x1157: file main.c, line 6.
```

```gdb
(gdb) break 8 if sum > 35
Breakpoint 4 at 0x1166: file main.c, line 8.
```

```gdb
(gdb) info break

Num     Type           Disp Enb Address            What
1       breakpoint     keep y   0x0000000000001189 in main at main.c:14
2       breakpoint     keep y   0x00000000000011a9 in main at main.c:18
3       breakpoint     keep y   0x0000000000001157 in sigma at main.c:6
4       breakpoint     keep y   0x0000000000001166 in sigma at main.c:8
        stop only if sum > 35
```
