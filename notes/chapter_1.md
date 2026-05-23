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
- Arithmetic operators combine values of numeric types.
- C performs automatic type conversion when an operator combines operands of two different types.
- The mod operator (`%`) can only take integer-type operands.
## 1.2. Input/Output (printf and scanf)
### 1.2.1. printf
- Placeholders consists of `%` followed by a type specifier letter.
- "Table 3"
### 1.2.2. scanf
- "Table 4"
## 1.3. Conditionals and Loops
- "Table 5"
- C supports multiway branching by chaining `if` and `else if` statements.
### 1.3.1. Boolean Values in C
- C doesn't provide a Boolean type with true or false values. Instead, integer values evaluate to *true* or *false* when used in conditional statements.
- When used in conditional expressions, any integer expression that is:
  - zero (0) evaluates to false.
  - nonzero (any positive or negative value) evaluates to true.
- The relational operators take operand(s) of the same type and evaluate to zero (false) or nonzero (true).
- C's logical operators take integer "Boolean" operand(s) and evaluate to either zero (false) or nonzero (true).
  - short-circuiting = stops evaluating at the first false expression.
- C's short-circuit logical operator evaluation stops evaluating a logical expression as soon the result is known.
- It's always best to use parentheses around complex Boolean expressions to make them easier to read.
### 1.3.2. Loops in C
#### while Loops
- "Table 6"
#### for Loops
- In C, `for` loops are more general looping constructs.
- "Table 7"
- The `for` loop evaluation rules are:
  - Evaluate initialization one time when first entering the loop.
  - Evaluate the boolean expression. If it's 0 (false), drop out of the `for` loop (that is, the program is done repeating the loop body statements).
  - Evaluate the statements inside the loop body.
  - Evaluate the step expression.
  - Repeat from step 2.
- `for` loops are a more natural language construct for definite loops (like iterating over a range of values), whereas `while` loops are a more natural language construct for indefinite loops (like repeating until the user enters an even number).
## 1.4. Functions
- Functions break code into manageable pieces and reduce code duplication.
- Functions might take zero or more parameters as input and they return a single value of a specific type.
- A function declaration or prototype specifies the function's name, its return type, and its parameter list (the number and types of all the parameters).
- A function definition includes the code to be executed when the function is called.
- All functions in C must be declared before they're called. This can be done by declaring a function prototype or by fully defining the function before calling it.
- A function call invokes a function, passing specific argument values for the particular call.
  - A function is called by its name and is passed arguments, with one argument for each corresponding function parameter.
- Arguments to C functions are passed by value: each function parameters is assigned the value of the corresponding argument passed to it in the function call by the caller. Pass by value semantics mean that any change to a parameter's value in the function (that is, assigning a parameter a new value in the function) is not visible to the caller.
### 1.4.1. The Stack
- The execution stack keeps track of the state of active functions in a program.
- Each function call creates a new stack frame (sometimes called an activation frame or activation record) containing its parameter and local variables values.
- The frame on the top of the stack is the active frame; it represents the function activation that is currently executing, and only its local variables and parameters are in scope.
- When a function is called, a new stack frame is created for it (pushed on the top of the stack), and space for its local variables and parameters is allocated in the new frame.
- When a function returns, its stack frame is removed from the stack (popped from the top of the stack), leaving the caller's stack frame on the top of the stack.
- "Figure 6"
