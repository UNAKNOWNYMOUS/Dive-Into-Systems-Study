---
id: chapter_2
aliases: []
tags: []
---

# 2. A Deeper Dive into C Programming
- Pointers provide a level of indirection to accessing program state, and dynamic memory allocation allows a program to adjust to changes in size and space needs as it runs, allocating more space as it needs it and freeing space it no longer needs.
- By understanding how and when to use pointer variables and dynamic memory allocation, a C programmer can design programs that are both powerful and efficient.
## 2.1. Parts of Program Memory and Scope
- A variable's scope defines when its name has meaning.
  - In other words, scope defines the set of program code blocks in which a variable is bound to (associate with) a program memory location and can be used by program code.
- Declaring a variable outside of any function body creates a global variable.
- Global variables remain permanently in scope and can be used by any code in the program because they're always bound to one specific memory location.
- Every global variable must have a unique name -- its name uniquely identifies a specific storage location in program memory for the entire duration of the program.
- Local variables and parameters are only in scope inside the function in which they are defined.
- Space to store a parameter's value is allocated on the stack when the function gets called, and it is deallocated from the stack when the function returns.
- Each activation of a function gets its own bindings for its parameters and local variables. Thus, for recursive function calls, each call (or activation) gets a separate stack frame containing space for its parameters and local variables.
- Because parameters and local variables are only in scope inside the function that defines them, different functions can use the same names for local variables and parameters.
- While there may occasionally be times when using global variables in C programs is necessary, we strongly recommend that you avoid programming with global variables whenever possible.
- Using only local variables and parameters yields code that's more modular, more general-purpose, and easier to debug.
- Also, because a function's parameters and local variables are only allocated in program memory when the function is active, they may result in more space-efficient programs.
- Upon launching a new program, the operating system allocates the new program's address space. A program's address space (or memory space) represents storage locations for everything it needs in its execution, namely storage for its instructions and data. A program's address space can be thought of as an array of addressable bytes; each used address in the program's address space stores all or part of a program instruction or data value (or some additional state necessary for the program's execution).
- "Figure 11"
- The top of a program's memory is reserved for use by the operating system, but the remaining parts are usable by the running program.
- The program's instructions are stored in the code section of the memory.
- Local variables and parameters reside in the portion of memory for the stack.
- Stack storage space for local variables and parameters exists only when the function is active (within the stack frame for the function's activation on the stack.)
- Global variables are stored in the data section. Unlike the stack, the data region does not grow or shrink -- storage space for global persists for the entire run of the program.
- Finally, the heap portion of memory is the part of a program's address space associated with dynamics memory allocation.
- [x] 2.1 Exercises
