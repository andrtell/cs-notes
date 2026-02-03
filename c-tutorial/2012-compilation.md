[Index](./index.md) [Prev](./2011-compilation.md) [Next](./2013-compilation.md)

----

__Library__

```c
// easymath.h

#ifndef EASYMATH_H
#define EASYMATH_H

int easymath_add(int a, int b);

#endif
```

```c
/// easymath.c

int easymath_add(int a, int b) {
	return a + b;
}
```

_compile_

```sh
cc -fPIC -shared -o libeasymath.so easymath.c
```

_install_

```sh
mkdir -p /usr/local/{lib,include}

cp easymath.h     /usr/local/include/
cp libeasymath.so /usr/local/lib/

# update the dynamic linker cache
ldconfig
```

__Program__

```c
/// main.c

#include <stdio.h>
#include <stdlib.h>

#include <easymath.h>

int main(void) {
  int a = rand() % 11;
  int b = rand() % 11;
  int c = easymath_add(a, b);
  printf("%d + %d = %d\n", a, b, c);
}
```

_compile_

```sh
cc -o main main.c -leasymath
```

_observe_

```sh
ldd ./main

libeasymath.so => /usr/local/lib/libeasymath.so
```

_run_

```sh
./main
6 + 10 = 16
```

__Reference__

https://refspecs.linuxfoundation.org/FHS_3.0/fhs/index.html

```
4.9. /usr/local : Local hierarchy

The /usr/local hierarchy is for use by the system administrator when installing software locally.

[...]

include/	Local C header files
lib/		Local libraries
```

_man 1 ldconfig_

```
DESCRIPTION

ldconfig  creates  the necessary links and cache to the most recent shared libraries
found in the directories specified on the command line, in the file /etc/ld.so.conf,
and in the trusted directories, /lib and /usr/lib.

The  cache  is used by the run-time linker, ld.so or ld-linux.so.  
```
