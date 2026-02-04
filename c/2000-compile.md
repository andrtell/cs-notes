[Index](./index.md) [Prev](./1104-basic-memory.md) [Next](./2001-compile.md)

----

__GCC Cheat Sheet__

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

__Example 1__

```sh
cc -g -Wall -Wextra -o program math.c -lm
```

__Example 2__

```sh
cc -fPIC -shared -o libeasy.so easy.c
```

__Example 3__

```sh
ls /not/the/usual/place/easy
libeasy.so
easy.h

export LIB_DIR=/not/the/usual/place/easy

cc -I $LIB_DIR \
   -L $LIB_DIR \
   program.c \
   -leasy \            # -leasy -> lib + easy + .so
   -Wl,-rpath,$LIB_DIR \
   -o program

ldd ./program
libeasy.so => /not/the/usual/place/easy/libeasy.so
```

__Example 4__

```sh
export LIB_DIR=/not/the/usual/place/easy

cc -I $LIB_DIR \
   -L $LIB_DIR \
   program.c \
   -leasy \
   -o program

./program

./program: error while loading shared libraries: libeasy.so: \
   cannot open shared object file: No such file or directory

export LD_LIBRARY_PATH=$LIB_DIR

./program
```



