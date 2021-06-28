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


# Definitions

## escape sequence
> An escape sequence like \n provides a general and extensible mechanism for representing hard-to-type or invisible characters. Among the others that C provides are \t for tab, \b for backspace. - The C Programming Language 2nd Edition, Brian Kernighan and Dennis Ritchie

## character string / string constant
> A sequence of characters in double quotes, like "hello, world\n" - The C Programming Language 2nd Edition, Brian Kernighan and Dennis Ritchie

## Program
> A C program, whatever its size, consists of functions and variables. - The C Programming Language 2nd Edition, Brian Kernighan and Dennis Ritchie

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
