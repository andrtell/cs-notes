[Index](./index.md) [Prev](./1106-memory.md) [Next](./1111-stucts.md)

----

Basic struct types and values.

----

```c
// main.c

#include <stdio.h>

struct Point {
  int x;
  int y;
};

int main() {
  struct Point p = {.x = 1, .y = 3};

  printf("Point is (%d, %d)\n", p.x, p.y);
}
```

_compile_

```sh
cc -o main main.c
```

_run_

```sh
./main
Point is: (1, 3)
```

---

Structs are copied by value.

---

```c
// main.c

#include <stdio.h>

struct Point {
  int x;
  int y;
};

int main() {
  struct Point p = {.x = 1, .y = 3};
  struct Point q = p;

  p.x = 7;
  p.y = 11;

  printf("p is (%d, %d), q is (%d, %d)\n", p.x, p.y, q.x, q.y);
}
```

_compile_

```sh
cc -o main main.c
```

_run_

```sh
./main
p is: (7, 11), q is: (1, 3)
```

---

Struct pointers are dereferenced using the `->` operator.

---

```c
// main.c

#include <stdio.h>

struct Point {
  int x;
  int y;
};

int main() {
  struct Point p = {.x = 1, .y = 3};
  struct Point *q = &p;

  printf("p is (%d, %d)\n", q->x, (*q).y);  // q->x is (*q).x
}

```

_compile_

```sh
cc -o main main.c
```

_run_

```sh
./main
p is: (1, 3)
```

---

Structs can be dynamically allocated.

---

```c
// main.c

#include <stdio.h>
#include <stdlib.h>

struct Point {
  int x;
  int y;
};

int main() {
   struct Point *p = malloc(sizeof(struct Point));

  if (p == NULL) {
    fprintf(stderr, "Memory allocation failed\n");
    return 1;
  }

  p->x = 1;
  p->y = 3;

  printf("p is (%d, %d)\n", p->x, p->y);
}
```

_compile_

```sh
cc -o main main.c
```

_run_

```sh
./main
p is: (1, 3)
```

---

Stack implemented on-top of linked list.

---

```c
#include <errno.h>
#include <stdbool.h>
#include <stddef.h>
#include <stdio.h>
#include <stdlib.h>

struct node {
	int 	     value;
	struct node *next;
};

struct stack {
	struct node *top;
};

int stack_init(struct stack **s) 
{
	if (s == NULL) {
		errno = EINVAL;
		return -1;
	}

	*s = malloc(sizeof(struct stack));

	if (*s == NULL) {
		errno = ENOMEM;
		return -1;
	}

	(*s)->top = NULL;

	return 0;
}

int stack_destroy(struct stack **s) 
{
	if (s == NULL || *s == NULL) {
		errno = EINVAL;
		return -1;
	}

	struct node *top = (*s)->top;
	struct node *next;
	
	while (top != NULL) {
		next = top->next;
		free(top);
		top = next;
	}

	free(*s);

	*s = NULL;

	return 0;
}

bool stack_is_empty(const struct stack *s) {
	return (s == NULL || s->top == NULL);
}

int stack_push(struct stack *s, int value) 
{
	if (s == NULL) {
		errno = EINVAL;
		return -1;
	}

	struct node *new_top = malloc(sizeof *new_top);

	if(new_top == NULL) {
		errno = ENOMEM;
		return -1;
	}

	new_top->value = value;
	new_top->next = s->top;

	s->top = new_top;

	return 0;
}

int stack_pop(struct stack *s, int *value) 
{
	struct node *tmp;

	if (s == NULL || value == NULL || s->top == NULL) {
		errno = EINVAL;
		return -1;
	}

	tmp = s->top;

	*value = tmp->value;
	s->top = tmp->next;

	free(tmp);

	return 0;
}

int stack_peek(const struct stack *s, int *value)
{
	if (s == NULL || value == NULL || s->top == NULL) {
		errno = EINVAL;
		return -1;
	}

	*value = s->top->value;

	return 0;
}

int main() {
	struct stack *s = NULL;

	int ret = stack_init(&s);

	if (ret == -1) {
		perror("Failed to create stack");
		return EXIT_FAILURE;
	}

	int vals[] = {1, 3, 7, 11, 13};
	size_t size = sizeof(vals)/sizeof(vals[0]);

	for (size_t i = 0; i < size; i++) {
		ret = stack_push(s, vals[i]);
		
		if (ret == -1) {
			perror("Push failed");
			stack_destroy(&s);
			return EXIT_FAILURE;
		}
	}

	int value;

	ret = stack_peek(s, &value);

	if (ret == -1) {
		perror("Peek failed");
		return EXIT_FAILURE;
	}
	
	printf("Top element is: %d\n", value);

	while (!stack_is_empty(s)) {
		ret = stack_pop(s, &value);
		if (ret == -1) {
			perror("Pop failed");
			return EXIT_FAILURE;
		}
		printf("Popped element: %d\n", value);
	}

	ret = stack_destroy(&s);

  if (ret == -1) {
    perror("Failed to destroy stack");
  }
}
```
