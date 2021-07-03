# Language

## /* \*/
Comment
> Any characters between /* and \*/ are ignored by the compiler; they may be used freely to make a program easier to understand. - The C Programming Language 2nd Edition, Brian Kernighan and Dennis Ritchie

## ++x
Increments the variable x by 1. Equivalent to 
```c
x = x + 1;
```

## if
> if statement tests the parenthesized condition, and if the condition is true, executes the statement (or group of statements in braces) that follows.  - The C Programming Language 2nd Edition, Brian Kernighan and Dennis Ritchie
```c
 #include <stdio.h>
 /* count lines in input */
 main()
 {
  int c;

  printf("Enter a capital letter to see if it's the first.\n");
  c = getchar();

  if (c == 'A') {
      printf("It is!\n");
  } else {
        printf("It is not!\n");
  }
 } 
 
$ ./a.out
>> Enter a capital letter to see if it's the first.
>>A
>> It is!
```

##getchar
> getchar() has no parameters. Every time you call it, it reads the next character of input and returns it to you. The function returns an int, being the ASCII code of the relevant character, but you can assign the result to a char variable if you want. - http://rabbit.eng.miami.edu/class/een218/getchar.html

> When you input something, it doesn't reach your C program until you press \n or send EOF (or EOL). - https://stackoverflow.com/questions/42223585/why-doesnt-getchar-read-characters-such-as-backspace

##main
> Normally you are at liberty to give functions whatever names you like, but 'main' is special - your program begins executing at the beginning of main. This means that every program must have a main somewhere.  - The C Programming Language 2nd Edition, Brian Kernighan and Dennis Ritchie

## stdio.h
> the standard input/output library

## \n
> the newline character, which when printed advances the output to the left margin on the next line - The C Programming Language 2nd Edition, Brian Kernighan and Dennis Ritchie

## EOF
>  a distinctive value when there is no more input, a value that cannot be confused with any real character. This value is called EOF, for ``end of file''. EOF is an integer defined in <stdio.h>, but the specific numeric value doesn't matter as long as it is not the same as any char value- The C Programming Language 2nd Edition, Brian Kernighan and Dennis Ritchie
> The value of EOF is always defined to be -1. That works well because all ASCII codes are positive, so it can't possibly clash with any real character's representation. - Stephen J. Murrell, http://rabbit.eng.miami.edu/class/een218/getchar.html

## \#define
Symbolic Constant
> A #define line defines a symbolic name or symbolic constant to be a particular string of characters  - The C Programming Language 2nd Edition, Brian Kernighan and Dennis Ritchie
```c
#define LOWER 1
#define UPPER 1000
```

##while
> The condition in parentheses is tested. If it is true, the body of the loop is executed. Then the condition is re-tested, and if true, the body is executed again. When the test becomes false (fahr exceeds upper) the loop ends, and execution continues at the statement that follows the loop. - The C Programming Language 2nd Edition, Brian Kernighan and Dennis Ritchie
```c
#include <stdio.h>

/* print the odd numbers between 1 and 10 */

#define LOWER 1
#define UPPER 10
#define STEP 2

int main()
{
  int counter;

  counter = LOWER;

  while (counter < UPPER) {
    printf("%d\n", counter);
    counter = counter + STEP;
  }
}

$ ./a.out
>> 1
>> 3
>> 5
>> 7
>> 9
```

##for
> The for statement is a loop, a generalization of the while.  Within the parentheses, there are three parts, separated by semicolons. The first part, the initialization is done once, before the loop proper is entered. The second part is the test or condition that controls the loop. This condition is evaluated; if it is true, the body of the loop is executed. Then the increment step is executed, and the condition re-evaluated. - The C Programming Language 2nd Edition, Brian Kernighan and Dennis Ritchie
```c
#include <stdio.h>

/* print the odd numbers between 1 and 10 */

#define LOWER 1
#define UPPER 10
#define STEP 2

int main()
{
  int counter;

  for (counter = LOWER; counter < UPPER; counter = counter + STEP) {
    printf("%d\n", counter);
  }
}

$ ./a.out
>> 1
>> 3
>> 5
>> 7
>> 9
```
##\
escape sequence
> An escape sequence like \n provides a general and extensible mechanism for representing hard-to-type or invisible characters. Among the others that C provides are \t for tab, \b for backspace. - The C Programming Language 2nd Edition, Brian Kernighan and Dennis Ritchie

##'' 
character constant
> A character surrounded by single quotes like 'a' is a character constant. A character constant is an integer whose value is the character code that stands for the character. - https://developerinsider.co/11-most-common-pitfalls-in-c-programming-language/

## ""
character string / string constant / string literal
> A sequence of characters in double quotes, like "hello, world\n" - The C Programming Language 2nd Edition, Brian Kernighan and Dennis Ritchie

> A string literal is an unmodifiable array whose elements are type char. The string in the double quotes plus terminating null-character are the contents, so "abc" has 4 elements ({'a', 'b', 'c', '\0'}) - https://developerinsider.co/11-most-common-pitfalls-in-c-programming-language/

##types
* int - integer
* float - floating point, may have fractional part
* char character - a single byte
* short short integer
* long long integer
* double double-precision floating point
- The C Programming Language 2nd Edition, Brian Kernighan and Dennis Ritchie

# Definitions

## Program
> A C program, whatever its size, consists of functions and variables. - The C Programming Language 2nd Edition, Brian Kernighan and Dennis Ritchie

##Text Stream
> A text stream is a sequence of characters divided into lines; each line consists of zero or more characters followed by a newline character. - The C Programming Language 2nd Edition, Brian Kernighan and Dennis Ritchie

# Concepts

## type arithmetic
> integer division truncates: any fractional part is discarded. - The C Programming Language 2nd Edition, Brian Kernighan and Dennis Ritchie

## Signed vs. Unsigned
> An int is signed by default, meaning it can represent both positive and negative values. An unsigned is an integer that can never be negative. If you take an unsigned 0 and subtract 1 from it, the result wraps around, leaving a very large number (2^32-1 with the typical 32-bit integer size). - http://soundsoftware.ac.uk/c-pitfall-unsigned.html

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
>> abc\n
>> 97
>> 98
>> 99
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
