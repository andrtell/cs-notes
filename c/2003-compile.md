[Index](./index.md) [Prev](./2002-compile.md) [Next](./2004-compile.md)

----

Comment on the `-g` flag.

----

__The program__

```c
// main.c

int main(void) {
  return 0;
}
```

_compile_

```sh
cc -g main.c
```

----

__Reference__

_man 1 gcc_

```
-g  Produce  debugging  information  in  the  operating  system's  native
    format  (stabs, COFF, XCOFF, or DWARF).

    GDB can work with this debugging information.

    On most systems that use stabs format, -g enables use of extra debugging
    information that  only  GDB  can  use;

    this  extra  information  makes debugging work better in GDB but probably
    makes other debuggers crash or refuse to read the program.

    If you want to control for certain whether to generate the extra information,
    use -gvms (see below).
```

https://en.wikipedia.org/wiki/Stabs

```
At one stage stabs was widely used on Unix systems, but the newer DWARF format has largely supplanted it. 
```
