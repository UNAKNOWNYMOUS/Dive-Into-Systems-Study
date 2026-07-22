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
## 2.2. C's Pointer Variables
- C's pointer variables provide a level of indirection to accessing program memory.
- C programmers can:
  - implement functions whose parameters can modify values in the caller's stack frame.
  - dynamically allocate (and deallocate) program memory at runtime when the program needs it.
  - efficiently pass large data structures to functions.
  - created linked dynamic data structures.
  - interpret bytes of program memory in different ways.
### 2.2.1. Pointer Variables
- A pointer variable stores the address of a memory location in which a value of a specific type can be stored.
- A pointer provides a level of indirection for accessing values stored in memory.
- "Figure 12"
- C programs most frequently use pointer variables for:
  - "Pass by pointer" parameters, for writing functions that can modify their argument's value through a pointer parameter.
- Dynamic memory allocation, for writing programs that allocate (and free) space as the program runs. Dynamic memory is commonly used for dynamically allocating arrays. It is useful when a programmer doesn't know the size of a data structure at compile time (e.g., the array size depends on a user input at runtime). It also enables data structures to be resized as the program runs.
#### Rules for Using Pointer Variables
- "Figure 13"
- All pointer variables can also be assigned a special value, NULL, which represents an invalid address.
- While a null pointer (one whose value is `NULL`) should never be used to access memory, the value `NULL` is useful for testing a pointer variable to see if it points to a valid memory address.
- "Figure 14"
- "Figure 15"
#### Pointer Examples
- If your program dereferences a pointer variable that does not contain a valid address, the program crashes.
- These types of errors exemplify one reason to initialize pointer variables to `NULL`; a program can then test a pointer's value for `NULL` before dereferencing it.
- [x] 2.2 Exercises
## 2.3. Pointers and Functions
- Pointer parameters provide a mechanism through which functions can modify argument values.
- The commonly used pass by pointer pattern uses a pointer function parameter that gets the value of the address of some storage location passed to it by the caller.
### Pass by Value
- "Figure 16"
- [x] 2.3 Exercises
## 2.4. Dynamic Memory Allocation
- Such dynamic memory allocation allows a C program to request more memory as it's running, and a pointer variable stores the address of the dynamically allocated space.
- Dynamic memory allocation grants flexibility to programs that:
  - do not know the size of arrays or other data structures until runtime (e.g. the size depends on user input)
  - need to allow for a variety of input sizes (not just up to some fixed capacity)
  - want to allocate exactly the size of data structures needed for a particular execution (don't waste capacity)
  - grow or shrink the sizes of memory allocated as the program runs, reallocating more space when needed and freeing up space when it's no longer required.
### 2.4.1. Heap Memory
- Every byte of memory in a program's memory space has an associated address.
- Everything the program needs to run is in its memory space, and different types of entities reside in different parts of a program's memory space.
- Because the stack and the heap grow at runtime (as functions are called and return and as dynamic memory is allocated and freed), they are typically far apart in a program's address space to leave a large amount of space for each to grow into as the program runs.
- "Figure 17"
- It's important to remember that heap memory is anonymous memory, where "anonymous" means that addresses in the heap are not bound to variable names.
### 2.4.2. malloc and free
- `malloc` and `free` are functions in the standard C library (`stdlib`) that a program call to allocate and deallocate memory in the heap.
- Heap memory must be explicitly allocated (malloc'ed) and deallocated (freed) by a C program.
- The `malloc` function returns a `void *` type, which represents a generic pointer to a non-specified type (or to any type).
- When a program calls `malloc` and assigns the result to a pointer variable, the program associates the allocated memory with the type of the pointer variable.
- A call to `malloc` fails if there is not enough free heap memory to satisfy the requested number of bytes to allocate.
- Because any call to `malloc` can fail, you should always test its return value for NULL (indicating `malloc`, failed) before dereferencing the pointer value.
- Dereferencing a NULL pointer will cause your program to crash!
- When a program no longer needs the heap memory it dynamically allocate with `malloc`, it should explicitly deallocate the memory by calling the `free` function.
- It's also a good idea to set the pointer's value to `NULL` after calling `free`, so that if an error in the program causes it to be accidentally dereferenced after the call to `free`, the program will crash rather than modify parts of heap memory that have been reallocated by subsequent calls to `malloc`.
- Such unintended memory references can result in undefined program behavior that is often very difficult to debug, whereas a null pointer dereference will fail immediately, making it a relatively easy bug to find and to fix.
### 2.4.3. Dynamically Allocated Arrays and Strings
- "Figure 18"
- Note that while `malloc` returns a pointer to dynamically allocated space in heap memory, C programs store the pointer to heap locations on the stack.
- The pointer variables contain only the base address (the starting address) of the array storage space in the heap.
- While a single call to `malloc` results in a chunk of memory of the requested number of bytes being allocated, multiple calls to `malloc` will not result in heap addresses that are contiguous (on most systems).
- "Table 10"
#### Heap Memory Management, malloc and free
- The C standard library implements `malloc` and `free`, which are the programming interface to its heap memory manager.
- When called, `malloc` needs to find a contiguous chunk of unallocated heap memory space that can satisfy the size of the request.
- The heap memory manager maintains a free list of unallocated extents of heap memory, where each extent specifies the start address and size of a contiguous un allocated chunk of heap space.
- Initially, all of heap memory is empty, meaning that the free list has a single extent consisting of the entire heap region.
- After a program has made some calls to `malloc` and `free`, heap memory can become fragmented, meaning that there are chunks of free heap space interspersed with chunks of allocated heap space.
- The heap memory manager typically keeps lists of different ranges of sizes of heap space to enable fast searching for a free extent of a particular size.
- In addition, it implements one or more policies for choosing among multiple free extents that could be used to satisfy a request.
- The `free` function may seem odd in that it only expects to receive the address of the heap space to free without needing the size of the heap space to free at that address. That's because `malloc` not only allocates the requested memory bytes, but it also allocates a few additional bytes right before the allocated chunk to store a header structure. The header stores metadata about the allocated chunk of heap space, such as size. As a result, a call to `free` only needs to pass the address of heap memory to free. The implementation of `free` can get the size of the memory to free from the header information that is in the memory right before the address passed to `free`.
### 2.4.4. Pointers to Heap Memory and Functions
- "Figure 19"
- [x] 2.4 Exercises
## 2.5. Arrays
### 2.5.1. Single-Dimensional Arrays
#### Statically Allocated
- Statically declared arrays are allocated either on the stack (for local variables) or in the data region of memory (for global variables).
#### Dynamically Allocated
- Calling the `malloc` function dynamically allocates an array on the heap at runtime. The address of the allocated heap space can be assigned to a global or local pointer variable, which then points to the first element of the array.
#### Array Memory Layout
- Whether an array is statically declared or dynamically allocated via a single call to `malloc`, array elements represent contiguous memory locations (addresses).
- The location of element `i` is at an offset `i` from the base address of the array.
- The exact address of the ith element depends on the number of bytes of the type stored in the array.
- There is no guarantee that the set of local variables are allocated to contiguous memory locations on the stack (hence, there could be a gap in the addresses between the end of `iarray` and the start of `carray`, as shown in this example.)
- Constants are often used when defining the total capacity of an array rather than using a literal numeric value. Constants are aliases for C literal values, and are used instead of literals to make the code easier to read and to allow for it to be more easily updated.
### 2.5.2. Two-Dimensional Arrays
- C supports multidimensional arrays.
#### Statically Allocated 2D Arrays
- "Figure 20"
- Programs often access the elements of a 2D array by iterating with nested loops.
### Two-Dimensional Array Parameters
- For multidimensional array parameters, you must indicate that the parameter is a multidimensional array, but you can leave the size of the first dimension unspecified (for good generic design). The sizes of other dimensions must be fully specified so that the compiler can generate the correct offsets into the array.
- The column dimension must be specified in the parameter definition of a 2D array so that the compiler can calculate the offset from the base address of the 2D array to the start of a particular row of elements. The offset calculation follows from the layout of 2D arrays in memory.
#### Two-Dimensional Array Memory Layout
- Statically allocated 2D arrays are arranged in memory in row-major order, meaning that all of row 0's elements come first, followed by all of row 1's elements, and so on.
- "Figure 21"
- Note that all array elements are allocated to contiguous memory addresses.
#### Dynamically Allocated 2D Arrays
#### Method 1: Memory-Efficient Allocation
- "Figure 22"
#### Method 1 (Single malloc) and Function Parameters
#### Methos 2: The Programmer-Friendly Way
- "Figure 23"
#### Method 2 (An Array of Arrays) and Function Parameters
