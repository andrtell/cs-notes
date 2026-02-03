[Index](./index.md) [Prev](./2001-compilation.md) [Next](./2003-compilation.md)

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
cc -o main main.c
```

__Reference__

_man 1 gcc_

```
-o <file>

   Place the primary output in file <file>.

   This applies to whatever sort of output is being produced, whether it be an executable file,
   an  object file, an assembler file or preprocessed C code.

   If -o is not specified, the default is to put an executable file in a.out, the object file
   for source.suffix in source.o, its assembler file in source.s, a precompiled header file
   in source.suffix.gch, and all preprocessed C source on standard output.
```
