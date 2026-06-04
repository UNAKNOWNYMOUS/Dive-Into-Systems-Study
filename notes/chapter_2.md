---
id: chapter_2
aliases: []
tags: []
---

# 2. A Deeper Dive into C Programming
- Pointers provide a level of indirection to accessing program state.
- Dynamic memory allocation allows a program to adjust to changes in size and space needs as it runs, allocating more space as it needs it and freeing space it no longer needs.
## 2.1. Parts of Program Memory and Scope
- A variable's scope defines when its name has meaning.
  - In other words, scope defines the set of program code blocks in which a variable is bound to (associated with) a program memory location and can be used by program code.
- Declaring a variable outside of any function body creates a *global variable*.
- Local variables and parameters are only in scope inside the function in which they are defined.
- While there may occasionally be times when using global variables in C programs is necessary, we strongly recommend that you avoid programming with global variables whenever possible.
- Using only local variables and parameters yields code that's more modular, more general-purpose, and easier to debug.
  - Also, because a function's parameters and local variables are only allocated in program memory when the function is active, they may result in more space-efficient programs.
- A program's address space (or memory space) represents storage locations for everything it needs in its execution, namely storage for its instructions and data.
- "Figure 11"
- The top of a program's memory is reserved for use by the operating system, but the remaining parts are usable by the running program.
- [x] 2.1 Exercises
## 2.2. C's Pointer Variables
- C's pointer variables provide a level of indirection to accessing program memory.
### 2.2.1. Pointer Variables
- A pointer variable stores the address of a memory location in which a value of a specific type can be stored.
- A pointer provides a level of indirection for accessing values stored in memory.
- "Figure 12"
- C programs most frequently use pointer variables for:
  - "Pass by pointer" parameters, for writing functions that can modify their argument's value through a pointer parameter.
  - Dynamic memory allocation.
#### Rules for Using Pointer Variables
- Declare a pointer variable.
- Initialize the pointer variable.
- "Figure 13"
- All pointer variables can also be assigned a special value, `NULL`, which represents an invalid address.
- A null pointer is one whose value is `NULL`.
- "Figure 14"
- Null pointers should never be dereferenced.
- Use the pointer variable.
- "Figure 15"
#### Pointer Examples
- If your program dereferences a pointer variable that does not contain a valid address, the program crashes.
- Initialize pointer variables to `NULL`!
  - A program can then text a pointer's value for `NULL` before dereferencing it.
- [x] 2.2 Exercises
## 2.3. Pointers and Functions
- Pointer parameters provide a mechanism through which functions can modify argument values.
- The commonly used pass by pointer pattern uses a pointer function parameter that gets the value of the address of some storage location passed to it by the caller.
- All arguments in C are passed by value and follow pass-by-value semantics: the parameter gets a copy of its argument value, and modifying the parameter's value does not change its argument's value.
  - In the pass-by-pointer pattern, the parameter still gets the value of its argument, but it is passed the value of an address. Just like in passing base types, changing a pointer parameter's value will not change its argument's value (that is, assigning the parameter to point to a different address will not change the argument's address value). However, by dereferencing a pointer parameter, the function can change the contents of memory that both the parameter and its argument refer to; through a pointer parameter, a function can modify a variable that is visible to the caller after the function returns.
- Steps for implementing and calling a function with a pass by pointer parameter:
  - Declare the function parameter to be a pointer to the variable type.
  - When making the function call, pass in the address of a variable as the argument.
  - In the body of the function, dereference the pointer parameter to change the argument's value.
- "Figure 16"
- [x] 2.3 Exercises
