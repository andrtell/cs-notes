[Index](./index.md) [Prev](./4000-debug.md) [Next](./4002-debug.md)

----

```c
// main.c

#include <stdio.h>

int main() {
    printf("Roses are red\n"
           "Violets are blue,\n"
           "Sugar is sweet\n"
           "And so are you.\n");
    return 0;
}
```

_compile_

```sh
cc -O0 -g -o main main.c
```

_debug_

```sh
gdb ./main
```

__GDB__

_redirect output_

```
(gdb) run > poem.txt

[Inferior 1 (process 111246) exited normally]
```

_shell command_

```
(gdb) !cat poem.txt

Roses are red
Violets are blue,
Sugar is sweet
And so are you.
```

----

[4.6 Your Program’s Input and Output](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Input_002fOutput.html#Input_002fOutput)
