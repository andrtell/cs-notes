[Index](./index.md) [Prev](./1103-memory.md) [Next](./1105-memory.md)

----

Thread local static memory with function scope

----

__The program__

```c
// fib.c

#include <stdio.h>

long long int fib() {
  static _Thread_local long long int a = 0;
  static _Thread_local long long int b = 1;
  long long c = a + b;
  a = b;
  b = c;
  return c;
}

int main() {
  for (int i = 2; i <= 15; i++) {
    printf("fib(%d) = %lli\n", i, fib());
  }
}
```

_compile_

```sh
cc -o fib fib.c
```

_run_

```
./fib

fib(2) = 1
fib(3) = 2
fib(4) = 3
fib(5) = 5
fib(6) = 8
fib(7) = 13
fib(8) = 21
fib(9) = 34
fib(10) = 55
fib(11) = 89
fib(12) = 144
fib(13) = 233
fib(14) = 377
fib(15) = 610
```
