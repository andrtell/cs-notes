[Index](./index.md) [Prev](./4001-debug.md) [Next](./4002-debug.md)

----

```c
// main.c

int main(void) {
  return 0;
}
```

```sh
# compile

cc -O0 -g -o main main.c
```

```sh
# debug

gdb -s ./main -e ./main

gdb -se ./main

gdb ./main
```

----

```gdb
(gdb) start

Temporary breakpoint 1, main () at main2.c:2
2		return 0;
```

----

From `(gdb) help running`

```
start -- Start the debugged program stopping at the beginning of the main procedure.
```

From `man 1 gdb`

```
-s file

Read symbol table from file.

-e file

Use file as the executable file to execute when appropriate,
and for examining pure data in conjunction with a core dump.

-se=<file>

Read symbol table from <file> and use it as the executable file.
```

