# Language

## /* \*/
Comment
> Any characters between /* and \*/ are ignored by the compiler; they may be used freely to make a program easier to understand. - The C Programming Language 2nd Edition, Brian Kernighan and Dennis Ritchie

## ++x
Increments the variable x by 1. Equivalent to 
```c
x = x + 1;
```

##printf
print formatted
>  printf is a general-purpose output formatting function. Its first argument is a string of characters to be printed, with each % indicating where one of the other (second, third, ...) arguments is to be substituted, and in what form it is to be printed. - The C Programming Language 2nd Edition, Brian Kernighan and Dennis Ritchie

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

## getchar()
> getchar() has no parameters. Every time you call it, it reads the next character of input and returns it to you. The function returns an int, being the ASCII code of the relevant character, but you can assign the result to a char variable if you want. - http://rabbit.eng.miami.edu/class/een218/getchar.html

> When you input something, it doesn't reach your C program until you press \n or send EOF (or EOL). - https://stackoverflow.com/questions/42223585/why-doesnt-getchar-read-characters-such-as-backspace

##1 and 0
true and false
> However, in C, the conditions true and false are represented by the integer values 1 and 0, respectively. - http://farside.ph.utexas.edu/teaching/329/lectures/node11.html

##;
> ...a statement can even be split over many lines, so long as its end is signaled by a semicolon. - http://farside.ph.utexas.edu/teaching/329/lectures/node11.html

## putchar(c)
> prints the contents of the integer variable c as a character, usually on the screen. - The C Programming Language 2nd Edition, Brian Kernighan and Dennis Ritchie

## main
> Normally you are at liberty to give functions whatever names you like, but 'main' is special - your program begins executing at the beginning of main. This means that every program must have a main somewhere.  - The C Programming Language 2nd Edition, Brian Kernighan and Dennis Ritchie

## stdio.h
> the standard input/output library

## !=
not equal to

## =
equal to

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

> A symbolic constant is a name that substitutes for a sequence of characters. The characters may represent either a number or a string. When a program is compiled, each occurrence of a symbolic constant is replaced by its corresponding character sequence. Symbolic constants are usually defined at the beginning of a program, by writing
   #define  NAME  text
where NAME represents a symbolic name, typically written in upper-case letters, and text represents the sequence of characters that is associated with that name. Note that text does not end with a semicolon, since a symbolic constant definition is not a true C statement. In fact, during compilation, the resolution of symbolic names is performed (by the C preprocessor) before the start of true compilation. For instance, suppose that a C program contains the following symbolic constant definition:
#define  PI  3.141593
Suppose, further, that the program contains the statement
area = PI * radius * radius;
During the compilation process, the preprocessor replaces each occurrence of the symbolic constant PI by its corresponding text. Hence, the above statement becomes
area = 3.141593 * radius * radius;
- http://farside.ph.utexas.edu/teaching/329/lectures/node11.html

## while
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

## for
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
## \
escape sequence
> An escape sequence like \n provides a general and extensible mechanism for representing hard-to-type or invisible characters. Among the others that C provides are \t for tab, \b for backspace. - The C Programming Language 2nd Edition, Brian Kernighan and Dennis Ritchie

## '' 
character constant
> A character surrounded by single quotes like 'a' is a character constant. A character constant is an integer whose value is the character code that stands for the character. - https://developerinsider.co/11-most-common-pitfalls-in-c-programming-language/

## ""
character string / string constant / string literal
> A sequence of characters in double quotes, like "hello, world\n" - The C Programming Language 2nd Edition, Brian Kernighan and Dennis Ritchie

> A string literal is an unmodifiable array whose elements are type char. The string in the double quotes plus terminating null-character are the contents, so "abc" has 4 elements ({'a', 'b', 'c', '\0'}) - https://developerinsider.co/11-most-common-pitfalls-in-c-programming-language/

# Definitions

## types
> C provides a variety of data types. The fundamental types are characters, and integers and floating point numbers of several sizes. In addition, there is a hierarchy of derived data types created with pointers, arrays, structures and unions.  - The C Programming Language 2nd Edition, Brian Kernighan and Dennis Ritchie

* int - integer
* float - floating point, may have fractional part
* char character - a single byte
* short short integer
* long long integer
* double double-precision floating point
- The C Programming Language 2nd Edition, Brian Kernighan and Dennis Ritchie

## program
> A C program, whatever its size, consists of functions and variables. - The C Programming Language 2nd Edition, Brian Kernighan and Dennis Ritchie

## declaration
> A declaration announces the properties of variables; it consists of a name and a list of variables, such as
```c
int fahr, celsius;
int lower, upper, step;
```
 - The C Programming Language 2nd Edition, Brian Kernighan and Dennis Ritchie

## assignment
> set the variables to their initial values
```c
lower = 0;
upper = 300;
step = 20;
```
 - The C Programming Language 2nd Edition, Brian Kernighan and Dennis Ritchie

## text stream
> A text stream is a sequence of characters divided into lines; each line consists of zero or more characters followed by a newline character. - The C Programming Language 2nd Edition, Brian Kernighan and Dennis Ritchie


## expressions and statements

### expression
> An expression represents a single data item--usually a number. The expression may consist of a single entity, such as a constant or variable, or it may consist of some combination of such entities, interconnected by one or more operators. Expressions can also represent logical conditions which are either true or false. However, in C, the conditions true and false are represented by the integer values 1 and 0, respectively. Several simple expressions are given below:
```c
a + b
x = y
t = u + v
x <= y
++j
```
- Text and Code from http://farside.ph.utexas.edu/teaching/329/lectures/node11.html 

> Expression: Something which evaluates to a value. Example: 1+2/x
The designers of C realized that no harm was done if you were allowed to evaluate an expression and throw away the result. In C, every syntactic expression can be a made into a statement just by tacking a semicolon along the end:
```c
1 + 2 / x;
```
...is a totally legit statement even though absolutely nothing will happen. 
- Code and Text from https://stackoverflow.com/questions/19132/expression-versus-statement

>  Expressions are formed from operators and operands; any expression, including an assignment or a function call, can be a statement.  - The C Programming Language 2nd Edition, Brian Kernighan and Dennis Ritchie

### statement
> A statement causes the computer to carry out some definite action. There are three different classes of statements in C: expression statements, compound statements, and control statements. An expression statement consists of an expression followed by a semicolon. The execution of such a statement causes the associated expression to be evaluated. A compound statement consists of several individual statements enclosed within a pair of braces { }. - http://farside.ph.utexas.edu/teaching/329/lectures/node11.html 

> Statement: A line of code which does something. Example: GOTO 100
- Code and Text from https://stackoverflow.com/questions/19132/expression-versus-statement

# Concepts

## control-flow contructions

> C provides the fundamental control-flow constructions required for well-structured programs: statement grouping, decision making (if-else), selecting one of a set of possible values (switch), looping with the termination test at the top (while, for) or at the bottom (do), and early loop exit (break). - The C Programming Language 2nd Edition, Brian Kernighan and Dennis Ritchie

## reserved words
This is a list of words that cannot be used as custom variable names:
> auto	else	long	switch break	enum	register	typedef case	extern	return	union char	float	short	unsigned const	for	signed	void continue	goto	sizeof	volatile default if	static	while do	int	struct	\_Packed double
- https://www.ibm.com/docs/en/adfz/developer-for-zos/14.2.0?topic=programs-c-reserved-keywords

## type arithmetic
> integer division truncates: any fractional part is discarded. - The C Programming Language 2nd Edition, Brian Kernighan and Dennis Ritchie

> char subtraction 
```c
#include <stdio.h>

int main() {
    printf("C is %i\n", 'c');
    printf("F is %i\n", 'f');
    printf("F - C is %i", 'f' - 'c');
    return 0;
}

$ ./a.out
>> C is 99
>> F is 102
>> F - C is 3
```
  

## Signed vs. Unsigned
> An int is signed by default, meaning it can represent both positive and negative values. An unsigned is an integer that can never be negative. If you take an unsigned 0 and subtract 1 from it, the result wraps around, leaving a very large number (2^32-1 with the typical 32-bit integer size). - http://soundsoftware.ac.uk/c-pitfall-unsigned.html

## ASCII
See table here:
https://www.cs.cmu.edu/~pattis/15-1XX/common/handouts/ascii.html

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
