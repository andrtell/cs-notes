
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

clean :
        rm edit $(objects)

```

Make has an implicit rule for updating a ‘.o’ file from a correspondingly named ‘.c’ file
using a ‘cc -c’ command. 

For example, it will use the recipe ‘cc -c main.c -o main.o’ to compile main.c into main.o. 

```makefile
objects = main.o kbd.o command.o

edit : $(objects)
        cc -o edit $(objects)

main.o : defs.h
        
kbd.o : defs.h command.h
        
command.o : defs.h command.h

.PHONY : clean     
clean :
        rm edit $(objects)

```
