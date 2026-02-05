
[Index](./index.md) [Prev](./2101-makefile.md) [Next](./2103-makefile.md)

----


```makefile
edit : main.o kbd.o command.o
        cc -o edit main.o kbd.o command.o

main.o : main.c defs.h
        cc -c main.c

kbd.o : kbd.c defs.h command.h
        cc -c kbd.c

command.o : command.c defs.h command.h
        cc -c command.c

clean :
        rm edit main.o kbd.o command.o

```
