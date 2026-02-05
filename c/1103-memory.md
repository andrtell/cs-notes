[Index](./index.md) [Prev](./1102-memory.md) [Next](./1104-memory.md)

----

Initialized static memory (.DATA)

----

__The program__

```c
// greet.c

#include <stdio.h>

// 1. Placed in the .data section.
// 2. OS reclaims the entire process address space on exit.
static char name[] = "PETER";

int main() {
  printf("Hello, %s\n", name);
}
```

_compile_

```sh
cc -o greet greet.c
```

_observe_

```sh
objdump -s -j .data ./greet

0000000000004010 <name>:
     4010:	50 45 54 45 52 00                                   PETER.
```

_run_

```
./greet

Hello, PETER!
```


