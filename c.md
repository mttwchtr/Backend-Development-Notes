# Language

## /* \*/
Comment
> Any characters between /* and \*/ are ignored by the compiler; they may be used freely to make a program easier to understand. - The C Programming Language 2nd Edition, Brian Kernighan and Dennis Ritchie

## main
> Normally you are at liberty to give functions whatever names you like, but 'main' is special - your program begins executing at the beginning of main. This means that every program must have a main somewhere.  - The C Programming Language 2nd Edition, Brian Kernighan and Dennis Ritchie

## stdio.h
> the standard input/output library

## \n
> the newline character, which when printed advances the output to the left margin on the next line - The C Programming Language 2nd Edition, Brian Kernighan and Dennis Ritchie

## \#define
Symbolic Constant
> A #define line defines a symbolic name or symbolic constant to be a particular string of characters  - The C Programming Language 2nd Edition, Brian Kernighan and Dennis Ritchie
```c
#define LOWER 1
#define UPPER 1000
```

# Definitions

## escape sequence
> An escape sequence like \n provides a general and extensible mechanism for representing hard-to-type or invisible characters. Among the others that C provides are \t for tab, \b for backspace. - The C Programming Language 2nd Edition, Brian Kernighan and Dennis Ritchie

## character string / string constant
> A sequence of characters in double quotes, like "hello, world\n" - The C Programming Language 2nd Edition, Brian Kernighan and Dennis Ritchie

## Program
> A C program, whatever its size, consists of functions and variables. - The C Programming Language 2nd Edition, Brian Kernighan and Dennis Ritchie

# Concepts

## ASCII
> In C programming, a character variable holds ASCII value (an integer number between 0 and 127) rather than that character itself. This integer value is the ASCII code of the character. For example, the ASCII value of 'A' is 65. What this means is that, if you assign 'A' to a character variable, 65 is stored in the variable rather than 'A' itself. - https://www.programiz.com/c-programming/examples/ASCII-value-character
```c
#include <stdio.h>
main()
{
   int c;
   c = getchar();
   while (c != 10) {
       printf("%d\n", c);
       c = getchar();
   }
} 

$ ./a.out
abc\n
97
98
99
```

# Tools

## cc
> clang is a C, C++, and Objective-C compiler which encompasses preprocessing, parsing, optimization, code generation, assembly, and linking. - man cc
```c
$ cc fahr.c -o fahr.out
$ ./fahr.out
```

# Programs

## Hello World
1. Create and populate hello.c
```c
#include <stdio.h>

main()
{
  printf("hello, world\n");
} 
```
2. From the terminal run. This creates a.out:
```zsh
$ cc hello.c
```
3. Execute this file from the terminal with:
```zsh
$ cc hello.c

>> hello, world
```
