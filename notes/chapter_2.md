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
## 2.4. Dynamic Memory Allocation
- In addition to pass-by-pointer parameters, programs commonly use pointer variables to dynamically allocate memory.
- Dynamic memory allocation grants flexibility to programs that:
  - do not know the size of arrays or other data structures until runtime (e.g. the size depends on user input)
  - need to allow for a variety of input sizes (not just up to some fixed capacity)
  - want to allocate exactly the size of data structures needed for a particular execution (don't wast capacity)
  - grow or shrink the sizes of memory allocated as the program runs, reallocating more space when needed and freeing up space when it's no longer required.
### 2.4.1. Heap Memory
- Every byte of memory in a program's memory space has an associated address.
- Everything the program needs to run is in its memory space, and different types of entities reside in different parts of a program's memory space.
- Because the stack and the heap grow at runtime (as functions are called and return and as dynamic memory is allocated and freed), they are typically far apart in a program's address space to leave a large amount of space for each to grow into as the program runs.
- "Figure 17"
- It's important to remember the heap memory is anonymous memory, where "anonymous" means that addresses in the heap are not bound to variable names.
### 2.4.2. malloc and free
- The `malloc` function returns a `void *` type, which represents a generic pointer to a non-specified type (or to any type).
- A call to `malloc` fails if there is not enough free heap memory to satisfy the requested number of bytes to allocate.
- Because any call to `malloc` can fail, you should always test its return value for NULL (indicating `malloc` failed) before dereferencing the pointer value. Dereferencing a NULL pointer will cause program to crash!
### 2.4.3. Dynamically Allocated Arrays and Strings
- "Figure 18"
- "Table 10"
#### Heap Memory Management, malloc and free
- When called, `malloc` needs to find a contiguous chunk of unallocated heap memory space that can satisfy the size of the request.
- The heap memory manager maintains a free list of unallocated extents of heap memory, where each extent specifies the start address and size of a contiguous unallocated chunk of heap space.
- Initially, all of heap memory is empty, meaning that the free list has a single extent consisting of the entire heap region. After a program has made some calls to `malloc` and `free`, heap memory can become fragmented, meaning that there are chunks of free heap space interspersed with chunks of allocated heap space. The heap memory manager typically keeps lists of different ranges of sizes of heap space to enable fast searching for a free extent of a particular size. In addition, it implements one or more policies for choosing among multiple free extents that could be used to satisfy a request.
- The `free` function may seem odd in that it only expects to receive the address of the heap space to free without needing the size of the heap space to free at that address. That's because `malloc` not only allocates the requested memory bytes, but it also allocates a few additional bytes right before the allocated chunk to store a header structure. The header stores metadata about the allocated chunk of heap space, such as the size. As a result, a call to `free` only needs to pass the address of heap memory to free. The implementation of `free` can get the size of the memory to free from the header information that is in memory right before the address passed to `free`.
### 2.4.4. Pointers to Heap Memory and Functions
- When passing a dynamically allocated array to a function, the pointer variable argument's value is passed to the function (i.e., the base address of the array in the heap is passed to the function).
- "Figure 19"
- [x] 2.4 Exercises
## 2.5. Arrays in C
### 2.5.1. Single-Dimensional Arrays
#### Statically Allocated
- Statically declared arrays are allocated either on the stack (for local variables) or in the data region of memory (for global variables).
#### Dynamically Allocated
- The address of the allocated heap space can be assigned to a global or local pointer variable, which then points to the first element of the array.
- Always check return value of functions and handle error return values.
#### Array Memory Layout
- Whether an array is statically declared or dynamically allocated via a single call to `malloc`, array elements represent contiguous memory locations (addresses).
- There is no guarantee that the set of local variables are allocated to contiguous memory locations on the stack (hence, there could be a gap in the addresses between variables).
- Constants are often used when defining the total capacity of an array rather than using a literal numeric value.
- Constants are aliases for C literal values, and are used instead of literals to make the code easier to read and to allow for it to be more easily updated.
### 2.5.2. Two-Dimensional Arrays
- C supports multidimensional arrays.
#### Statically Allocated 2D Arrays
- "Figure 20"
#### Two-Dimensional Array Parameters
