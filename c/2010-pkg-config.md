[Index](./index.md) [Prev](./2009-compile.md) [Next](./2101-makefile.md)

----

Using `pkg-config` to generate build dependencies

----

__The program__

```c
// main.c

#include <curl/curl.h>

int main(void) {
	curl_global_init(CURL_GLOBAL_DEFAULT);
}
```

_compile_

```sh
cc main.c `pkg-config --cflags --libs libcurl`
```

_observe output of pkg-config_

```sh
pkg-config --cflags --libs libcurl

-I/usr/include/x86_64-linux-gnu -lcurl
```

----

__References__

_man 1 pkg-config_

```
NAME

pkgconf — a system for configuring build dependency information

QUERY-SPECIFIC OPTIONS

  --cflags, --cflags-only-I, --cflags-only-other

    Display either all CFLAGS, only -I CFLAGS or only CFLAGS that are not -I.

  --libs, --libs-only-L, --libs-only-l, --libs-only-other

    Display either all linker flags, only -L linker flags, only -l linker flags
    or only linker flags that are not -L or -l.

```
