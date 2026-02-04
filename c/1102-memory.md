[Index](./index.md) [Prev](./1101-memory.md) [Next](./1102-memory.md)

----

Un-uninitialized static memory (.BSS)

----

__Program source__

```c
// greet.c

#include <stdio.h>

// 1. Placed in the .bss section and is zero-filled automatically by the OS/loader before main() starts.
//    (i.e name[0] = \0, name[1] = \0, ...)
//
// 2. OS reclaims the entire process address space on exit.
static char name[100]; 

int main() {
  scanf("%s", name);
  printf("Hello, %s\n", name);
}
```

_compile_

```sh
cc -o greet greet.c
```

_run_

```
./greet

Peter<ENTER>
Hello, Peter!
```
