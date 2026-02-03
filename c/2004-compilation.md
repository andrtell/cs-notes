[Index](./index.md) [Prev](./2003-compilation.md) [Next](./2005-compilation.md)

----

__Program__

```c
// main.c

int main(void) {
  return 0;
}
```

_compile_

```sh
cc -std=gnu18 main.c
```

__Reference__

_man 1 gcc_

```
-std=
    Determine the language standard.

    This option is currently only supported when compiling C or C++.

    [...]

    gnu17
    gnu18
        GNU dialect of ISO C17.  This is the default for C code.
```
