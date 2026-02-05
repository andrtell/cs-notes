
[Index](./index.md) [Prev](./2101-makefile.md) [Next](./3001-GDB.md)

----

Simple Makefile

----

```makefile
main : main.o extra.o
        cc -o main main.o extra.o

main.o : main.c defs.h
        cc -c main.c

extra.o : extra.c defs.h extra.h
        cc -c extra.c

.PHONY : clean

clean :
        rm main main.o extra.o

```

----

Variables can be used in a Makefile

----

```makefile
CFLAGS  = -g -Wall -Wextra

OBJECTS = main.o extra.o

main : $(OBJECTS)
        cc -o main $(OBJECTS)

main.o : main.c defs.h
        cc $(CFLAGS) -c main.c

extra.o : extra.c defs.h extra.h
        cc $(CFLAGS) -c extra.c

.PHONY : clean

clean :
        rm main $(OBJECTS)

```

----

Make can deduce prerequisites and recipes in rules.

----

```makefile
CFLAGS  = -g -Wall -Wextra 

OBJECTS = main.o extra.o

main : $(OBJECTS)

main.o : defs.h

extra.o : defs.h extra.h
        
.PHONY : clean

clean :
        rm main $(OBJECTS)
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
main : main.o extra.o
```

into

```makefile
main: main.o extra.o
        $(CC) $(LDFLAGS) main.o extra.o $(LOADLIBES) $(LDLIBS)
```

See [10 Using Implicit Rules](https://www.gnu.org/software/make/manual/make.html#Implicit-Rules) from the GNU Make manual.
