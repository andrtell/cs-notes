[Index](./index.md) [Prev](./1104-memory.md) [Next](./2002-compile.md)

----

GCC Cheat Sheet

---

| GCC Flag           | Descriptions                            | Examples                              | References      |
| ------------------ | --------------------------------------- | ------------------------------------- | --------------- |
| -c                 | Compile but do not link.                | cc -c                                 | man 1 gcc       |
| -g                 | Add debug information.                  | cc -g                                 |                 |
| -o _file_          | Place the primary output in _file_.     | cc -o main                            |                 |
| -std=_standard_    | Set the language standard               | cc -std=gnu17                         |                 |
|                    | -std=_gnu17_ is the default for C.      |                                       |                 |
| -O0, -O1, -O2, -O3 | Set the level of optimization           | cc -O3                                |                 |
|                    | -O0 is the default.                     |                                       |                 |
| -Wall              | Enables all the warnings                | cc -Wall                              |                 |
| -Wextra            | Enables some extra warnings             | cc -Wextra                            |                 |
|                    | (same as -W)                            |                                       |                 |
| -l _library_       | Link with _library_                     | cc math.c -lm                         |                 |
| -I _dir_           | Add _dir_ to the list of directories    |                                       |                 |
|                    | to be searched for header files.        |                                       |                 |
| -L _dir_           | Add _dir_ to the list of                |                                       |                 |
|                    | directories to be searched for -l.      |                                       |                 |
| -Wl,option         | Pass option as an option to the linker. | cc -Wl,-rpath,$LIB_DIR                | man 1 ld        |
| -shared            | Produce  a  shared  object              | cc -shared -fPIC -o libeasy.so easy.c |                 |

---

Quick examples

----

I. Compiling a program and linking it to a library.

```sh
cc -g -Wall -Wextra -o program math.c -lm
```

II. Compiling a library / shared object.

```sh
cc -fPIC -shared -o libeasy.so easy.c
```

III. Compiling and linking a program to a library in a non-standard location.

```sh
export LIB_DIR=/not/the/usual/place/easy

cc -I $LIB_DIR \
   -L $LIB_DIR \
   program.c \
   -leasy \            # -leasy -> lib + easy + .so
   -Wl,-rpath,$LIB_DIR \
   -o program
```

_observe linkage_

```sh
ldd ./program
libeasy.so => /not/the/usual/place/easy/libeasy.so
```

IV. Compiling a library and making use of `SONAME` to create a versioned copy.

```sh
cc -fPIC -shared \
   -Wl,-soname,libeasy.so.1 \
   -o libeasy.so.1.0.0 \
   easy.c
```


