
[Index](./index.md) [Prev](./2101-makefile.md) [Next](./2103-makefile.md)

----

Simple Makefile

----

```makefile
program : main.o extra.o
        cc -o program main.o extra.o

main.o : main.c defs.h
        cc -c main.c

extra.o : extra.c defs.h extra.h
        cc -c extra.c

.PHONY : clean

clean :
        rm program main.o extra.o

```

----

Make variables

----

```makefile
objects = main.o extra.o

program : $(objects)
        cc -o program $(objects)

main.o : main.c defs.h
        cc -c main.c

extra.o : extra.c defs.h extra.h
        cc -c extra.c

.PHONY : clean

clean :
        rm edit $(objects)

```

----

Make can deduce prerequisites and recipes in rules.

----

```makefile
objects = main.o extra.o

program : $(objects)
        cc -o program $(objects)

main.o : defs.h
        
extra.o : defs.h extra.h
        
.PHONY : clean

clean :
        rm edit $(objects)
```

In the above example a recipe for compiling C is constructed from `$(CC) $(CPPFLAGS) $(CFLAGS) -c`.



