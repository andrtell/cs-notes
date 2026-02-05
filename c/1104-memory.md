[Index](./index.md) [Prev](./1103-memory.md) [Next](./1105-memory.md)

----

Static memory with function scope

----

__The program__

```c
// fib.c

#include <stdio.h>

long long int fib() {
  static long long int a = 0;
  static long long int b = 1;
  long long c = a + b;
  a = b;
  b = c;
  return c;
}

int main() {
  for (int i = 0; i < 20; i++) {
    printf("fib(%d) = %lli\n", i, fib());
  }
}
```

_compile_

```sh
cc -o fib fib.c
```

_observe_

```sh
objdump -s -j .data ./greet

0000000000004010 <name>:
     4010:	50 45 54 45 52 00                                   PETER.
```

_run_

```
./fib


```


