
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

main.o : defs.h
        
extra.o : defs.h extra.h
        
.PHONY : clean

clean :
        rm edit $(objects)
```

In the above Make transforms the rule:

```makefile
main.o : defs.h
```

into

```makefile
main.o : main.c defs.h
        $(CC) $(CPPFLAGS) $(CFLAGS) -c main.c
```

and the rule:

```makefile
program : $(objects)
```

into

```makefile
program: $(objects)
        $(CC) $(LDFLAGS) n.o $(LOADLIBES) $(LDLIBS)
```



