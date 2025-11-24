The basic operation of Make is to find the name of a  needed target in the description, ensure that all of the  files on which it depends exist and are up to date, and  then create the target if it has not been modified since  its generators were. The description file really defines  the graph of dependencies; Make does a depth-first search of this graph to determine what work is really necessary.

Use a file called a "Makefile" that contains dependency information, rule for re-crearting target files, including calling [[gcc]]

### Example
You have a program named ksf. It is compiled and  
linked from several components:  
ksf.c – the main program  
ksf_ui.c – the user-interface code  
ksf_data.c – global data definitions  
ksf_db.c – interface to mySQL database  
ksf.h – macros and definitions included by all .c files

```
CFLAGS=-std=c99 -Wall -pedantic -Wextra -Werror -O2 \  
-Wstrict-prototypes -Wold-style-definition –g  
ksf: ksf.o ksf_ui.o ksf_data.o ksf_db.o  
gcc $(CFLAGS) –o ksf ksf.o \  
ksf_ui.o ksf_data.o ksf_db.o  
ksf.o: ksf.c ksf.h  
gcc –c $(CFLAGS) ksf.c  
ksf_ui.o: ksf_ui.c ksf.h  
gcc –c $(CFLAGS) ksf_ui.c  
ksf_data.o: ksf_data.c ksf.h  
gcc –c $(CFLAGS) ksf_data.c  
ksf_db.o: ksf_db.c  
gcc –c $(CFLAGS) ksf_db.c
```

### See also
[[C]]
[[gcc]]