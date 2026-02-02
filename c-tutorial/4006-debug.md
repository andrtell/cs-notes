```
<linenum>

    Specifies the line number <linenum> of the current source file.

    example: (gdb) break 2

[...]

<filename>:<linenum>

    Specifies the line <linenum> in the source file <filename>.

    example: (gdb) break main.c:2

[...]

<function>

    Specifies the line that begins the body of the function <function>.

    example: (gdb) break main

[...]

<filename>:<function>

    Specifies the line that begins the body of the function <function> in the file <filename>.

    example: (gdb) break main.c:main
```
