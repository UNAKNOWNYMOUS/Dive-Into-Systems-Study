---
id: chapter_1
aliases: []
tags: []
---

# 1. By the C, by the C, by the Beautiful C
- C is a high-level programming language.
- C is an imperative and a procedural programming language, which means that a C program is expressed as a sequence of statements (steps) for the computer to execute and that C programs are structured as a set of functions (procedures).
- Every C program must have at least one function, the `main` function, which contains the set of statements that execute when the program begins.
- The C programming language is less abstracted from the computer's machine language.
- C makes it easier for a programmer to see and understand the relationship between a program's code and the computer's execution of it.
- C programmers retain more control over how their programs execute on the hardware, and they can write code that runs more efficiently than equivalent code written using the high-level abstractions provided by other programming languages.
  - In particular, they have more control over how their programs manage memory, which can have a significant impact on performance.
- Thus, C remains the *de facto* language for computer systems programming where low-level control and efficiency are crucial.
## 1.1. Getting Started Programming in C
- "Table 1"
- All `#include` statements appear at the top of the program outside of function bodies.
- The `main` function returns the `int` value 0 to signify running to completion without error.
- The `void` means it doesn't expect to receive a parameter.
- In C, statements must be within the body of some function.
### 1.1.1. Compiling and Running C Programs
- "Figure 4"
- A C *compiler* is a program that translates C source code into a *binary executable* form that the computer hardware can directly execute.
  - A binary executable consists of a series of 0's and 1's in a well-defined format that a computer can run.
- GCC by default produces a binary executable name `a.out`.
- "Figure 5"
#### Detailed Steps
- Often when compiling with `gcc`, you want to include several command line options.
- Because the `gcc` command line can be long, frequently the `make` utility is used to simplify compiling C programs and for cleaning up filed created by `gcc`.
- [Learn Make] (https://www.cs.swarthmore.edu/~newhall/unixhelp/howto_makefiles.html)
### 1.1.2. Variables and C Numeric Types
- C uses variables as named storage locations for holding data.
- Thinking about the *scope* and *type* of program variables is important to understand the semantics of what your program will do when you run it.
- A variable's *scope* defines when the variable has meaning (that is, where and when in your program it can be used) and its lifetime (that is, it could persist for the entire run of a program or only during a function activation).
- A variable's *type* defines the range of values that it can represent and how those values will be interpreted when performing operations on its data.
- In C, all variables must be declared before they can be used.
- A variable can only have a single *type*.
- Initialize variables before using their value.
- Integer division truncates after the decimal.
### 1.1.3. C Types
- A string literal is any sequence of characters between double quotes.
- In C, a string and a `char` are two very different types, and they evaluate differently.
#### C Numeric Types
- "Table 2"
- The C standard doesn't specify whether the `char` type is signed or unsigned. As a result, some implementations might implement `char` as signed integer values and others as unsigned.
  - It's good programming practice to explicitly declare `unsigned char` if you want to use the unsigned version of a `char` variable.
- The exact number of bytes for each of the C types might vary from one architecture to the next. The sizes in "Table 2" are minimum (and common) sizes for each type.
#### Arithmetic Operators
- C performs automatic type conversion when an operator combines operands of two different types.
- The mod operator (`%`) can only take integer-type operands.
