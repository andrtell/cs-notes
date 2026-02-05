[Index](./index.md) [Prev](./1001-hello-world.md) [Next](./1102-memory.md)

----

Automatic memory (STACK).

----

__The program__

```c
// greet.c

#include <stdio.h>

int main(void) {
	// 100 chars allocated on the stack on each call (automatic storage).
	char name[100];     

	// char[] decays to a pointer char * to its first element char[0].
	scanf("%s", name);  

	printf("Hello, %s!\n", name);

	// name is automatically deallocated here (stack frame cleanup)
	return 0;
}
```

_compile_

```sh
cc -o greet greet.c
```

_run_

```sh
./greet

Peter<ENTER>
Hello, Peter!
```
