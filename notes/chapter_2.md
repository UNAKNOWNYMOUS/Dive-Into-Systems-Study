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
