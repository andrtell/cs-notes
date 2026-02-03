[Index](./index.md) [Prev](./1001-hello-world.md) [Next](./1102-basic-memory.md)

----

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

----

```sh
# compile

 cc -o greet greet.c
```

```sh
# run

 ./greet
 Peter<ENTER>
 Hello, Peter!
```
