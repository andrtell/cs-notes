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
