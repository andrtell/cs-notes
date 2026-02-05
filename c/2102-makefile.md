
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


```makefile
objects = main.o kbd.o command.o

edit : $(objects)
        cc -o edit $(objects)

main.o : main.c defs.h
        cc -c main.c

kbd.o : kbd.c defs.h command.h
        cc -c kbd.c

command.o : command.c defs.h command.h
        cc -c command.c

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
