---
id: chapter_1
aliases: []
tags: []
---

# 1. By the C, by the C, by the Beautiful C
- C is a high-level programming language like other languages you might know.
- C is an imperative and procedural programming language, which means that a C program is expressed as a sequence of statements (steps) for the computer to execute and that C programs are structured as a set of functions (procedures).
- C's lack of high-level abstractions might make it seem like a less appealing programming language to use.
  - However, being less abstracted from the underlying machine makes C easier for a programmer to see and understand the relationship between a program's code and the computer's execution of it.
- C programmers retain more control over how their programs execute on the hardware, and they can write code that runs more efficiently than equivalent code written using the high-level abstractions provided by other programming languages.
## 1.1. Getting Started Programming in C
- "Table 1"
### 1.1.1. Compiling and Running C Programs
- "Figure 4"
- To run a C program, it must first be translated into a form that a computer system can directly execute.
- A C compiler is a program that translates C source code into a binary executable form that the computer hardware can directly execute.
- A binary executable consists of a series of 0's and 1's in a well-defined format that a computer can run.
- "Figure 5"
#### Detailed Steps
- Often when compiling with `gcc`, you want to include several command line options. For example, these options enable more compiler warnings and build a binary executable with extra debugging information. `gcc -Wall -g -o hello hello.c`
- Because the `gcc` command line can be long, frequently the `make` utility is used to simplify compiling C programs and for cleaning up files created by `gcc`. [Using make and writing Makefiles](https://www.cs.swarthmore.edu/~newhall/unixhelp/howto_makefiles.html) are important skills that you develop as you build up experience with C programming.
### 1.1.2. Variables and C Numeric Types
- C uses variables as named storage locations for holding data.
- Thinking about the scope and type of program variables is important to understand the semantics of what your program will do when you run it.
- A variable's scope defines when the variable has meaning (that is, where and when in your program it can be used) and its lifetime (that is, it could persist for the entire run of a program or only during a function activation).
- A variable's type defines the range of values that it can represent and how those values will be interpreted when performing operations on its data.
- In C, all variables must be declared before they can be used.
- A variable can only have a single type.
- By convention, C variables should be declared at the beginning of their scope (at the top of a `{}` block), before any C statements in that scope.
- C statements are delineated by `;`.
### 1.1.3. C Types
- A string literal is any sequence of characters between double quotes.
#### C Numeric Types
- "Table 2"
- The C standard doesn't specify whether the `char` type is signed or unsigned.
  - As a result, some implementations might implement `char` as signed integer values and other as unsigned.
  - It's good programming practice to explicitly declare `unsigned char` if you want to use the unsigned version of a `char`.
- The exact number of bytes for each of the C types might vary from one architecture to the next. The sizes in "Table 2" are minimum (and common) sizes for each type.
#### Arithmetic Operators
- C performs automatic type conversion when an operator combines operands of two different types.
## 1.2. Input/Output (printf and scanf)
### 1.2.1. printf
- "Table 3"
### 1.2.2. scanf
- "Table 4"
- Prefixing the name of a variable with the `&` operator produces the location of that variables in the program's memory -- the memory address of the variable.
## 1.3. Conditionals and Loops
- "Table 5"
- In C, the `else` part is optional.
### 1.3.1. Boolean Values in C
- C doesn't provide a Boolean type with true or false values.
  - Instead, integer values evaluate to true or false when used in conditional statements.
- When used in conditional expressions, any integer expression that is:
  - zero (0) evaluates to false
  - nonzero (any positive or negative value) evaluates to true
- C has a set of relational and logical operators for Boolean expressions.
- The relational operators take operand(s) of the same type and evaluate to zero (false) or nonzero (true).
- C's logical operators take integer "Boolean" operand(s) and evaluate to either zero (false) or nonzero (true).
- C's short-circuit logical operator evaluation stops evaluating a logical expression as soon as the result is known.
- It's always best to use parentheses around complex Boolean expressions to make them easier to read.
### 1.3.2. Loops in C
#### while Loops
- "Table 6"
#### for Loops
- In C, `for` loops are more general looping constructs.
- "Table 7"
- The C `for` loop evaluation rules are:
  - Evaluate initialization one time when first entering the loop.
  - Evaluate the boolean expression. If it's 0 (false), drop out of the `for` loop (that is, the program is done repeating the loop body statements).
  - Evaluate the statements inside the loop body.
  - Evaluate the step expression.
  - Repeat from step (2),
- In C, `for` loops and `while` loops are equivalent in power, meaning that any `while` loop can be expressed as a `for` loop, and vice versa.
- Because `for` and `while` loops are equally expressive in C, only one looping construct is needed in the language. However, `for` loops are a more natural language construct for definite loops (like iterating over a range of values), whereas `while` loops are a more natural language construct for indefinite loops (like repeating until the user enters an even number). As a result, C provides both to programmers.
