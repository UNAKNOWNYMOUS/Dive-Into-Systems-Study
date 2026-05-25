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
## 1.5. Arrays and Strings
- An array is a C construct that creates an ordered collection of data elements of the same type and associates this collection with a single program variable.
- Ordered means that each element is in a specific position in the collection of values (that is, there is an element in position 0, position 1, and so on), not that the values are necessarily sorted.
- Arrays come in several flavors, but the basic form is a one-dimensional array, which is useful for implementing list-like data structures and strings in C.
### 1.5.1. Introduction to Arrays
- C arrays can store multiple data values of the same type.
- Statically declared arrays, meaning that the total capacity (the maximum number of elements that can be stored in an array) is fixed and is defined when the array variable is declared.
- C exposes a low-level array implementation to the programmer and leaves it up to the programmer to implement higher-level functionality.
- "Table 8"
- In C, individual array elements are allocated in consecutive locations in the program's memory.
### 1.5.2. Array Access Methods
- Access to array element beyond the bounds of the allocated array, the program's runtime behavior is undefined.
- The C compiler is happy to compile code that accesses array positions beyond the bounds of the array; there is no bounds checking by the compiler or at runtime.
### 1.5.3. Arrays and Functions
- In C, the name of the array variable is equivalent to the base address of the array (that is, the memory location of its 0th element).
- "Figure 7"
### 1.5.4. Introduction to Strings and the C String Library
- In C, strings are implemented as arrays of `char` values. Not every character array is used as a C String, but every C string is a character array.
- Strings in C must end with a special character value, the null character (`'\0'`), to indicate the end of the string.
  - Strings that end with a null character are said to be null-terminated.
- Note that most C string library functions expect the call to pass in a character array that has enough capacity for the function to perform its job if not doing so will lead to undefined behavior in your program.
- C string library functions also require that string values passed to them are correctly formed, with a terminating `\0` character if not functions could continue beyond the end of the array's bounds, leading to undefined behavior that could cause it to crash.
## 1.6. Structs
- Arrays and structs are the two ways in which C supports creating collections of data elements.
- Arrays are used to create an ordered collection of data elements of the same type, whereas structs are used to create a collection of data elements of different types.
- C is not an object-oriented programming language.
  - It does, however, support defining structured types, which are like the data part of classes.
- A `struct` is a type used to represent a heterogeneous collection of data; it's a mechanism for treating a set of different types as a single, coherent unit.
- There are three steps to defining and using `struct` types in C programs:
  - Defining a new `struct` type that represents the structure.
  - Declare variables of the new `struct` type.
  - Use dot (`.`) notation to access individual field values of the variable.
### 1.6.1. Defining a Struct Type
- A struct type definition should appear outside of any function, typically near the top of the program's `.c` file.
### 1.6.2. Declaring Variables of Struct Types
- Note that unlike the other types we've encountered so far that consist of a single word, the name of our new struct type is two words.
### 1.6.3 Accessing Field Values
- To access field values in a struct variable, use dot notation.
- "Table 9"
- "Figure 8"
- C struct types are lvalues, meaning they can appear on the left side of an assignment statement.
- "Figure 9"
#### lvalues
- An lvalue is an expression that can appear on the left side of an assignment statement.
- An lvalue is something assignable because it represents a memory location. Variables, struct field, and array elements are lvalues. A fixed array name is not assignable (because the array name is a fixed base address, you can change the elements of the array, but you cannot change where the array itself lives in memory).
### 1.6.4. Passing Structs to Functions
- In C, arguments of all types are passed by value to functions.
- "Figure 10"
- Understanding the pass-by-value semantics of struct parameters is particularly important when a struct contains a statically declared array field. When such a struct is passed to a function, the struct argument's entire memory contents, including every array element in the array field, is copied to its parameter. If the parameter struct's array contents are changed by the function, those changes will not persist after the function returns. This behavior might seem odd given what we know about how arrays are passed to functions, but it's consistent with the struct-copying behavior described earlier.
## 1.7. Summary
