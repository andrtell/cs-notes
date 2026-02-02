[Index](./index.md) [Prev](./3005-debug.md) [Next](./3007-debug.md)

----

```c
// main.c

#include <stdio.h>
#include <signal.h>
#include <unistd.h>

volatile sig_atomic_t running = 1;

void handle_sigint(int sig) {
  (void)sig;
  running = 0;
}

int main(void) {
  signal(SIGINT, handle_sigint);

  setbuf(stdout, NULL);

  printf("Started with PID: %d\n", getpid());

  while (running) {
    printf(".");
    sleep(1);
  }

  return 0;
}
```

```sh
# compile

cc -O0 -g -o main main.c
```

```sh
# run

./main

Started with PID: 113247
```

```sh
# debug (in second terminal)

gdb
```

----

```gdb
(gdb) attach 113247
```

```gdb
(gdb) break main.c:22

Breakpoint 1 at 0x6454099ac24e: file main.c, line 22.
```

```gdb
(gdb) continue

Breakpoint 1, main () at main.c:22
22		printf(".");
```

```gdb
(gdb) print running

$1 = 1
```

```gdb
(gdb) kill

[Inferior 1 (process 113247) killed]
```

----

Allow attach until next boot

```sh
echo 0 | sudo tee /proc/sys/kernel/yama/ptrace_scope
```
