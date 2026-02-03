[Index](./index.md) [Prev](./2005-compilation.md) [Next](./2007-compilation.md)

----

```c
// main.c

int main(void) {
	int answer = 42;
}
```

_compile_

```sh
cc -Wall -Wextra main.c

main.c: In function ‘main’:
main.c:2:13: warning: unused variable ‘answer’ [-Wunused-variable]
    2 |         int answer = 42;
      |             ^~~~~~
```

_man 1 gcc_

```
-Wall
    This enables all the warnings about constructions that some users consider questionable,
    and that are easy to avoid (or modify  to  prevent  the warning), even in conjunction
    with macros.

-Wextra
    This  enables some extra warning flags that are not enabled by -Wall.

    (This option used to be called -W.  The older name is still supported,
     but the newer name is more descriptive.)
```

