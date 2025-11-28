 #pp 

# Dynamic Memory Allocation 

Vars and arrays provide fixed size allocation 
- requirement to dynamically request variable sized blocks from runtime system 
- requests memory at runtime 

# Memory Layout 

![[Screenshot 2025-11-03 at 15.56.09.png]]

**Stack**:
- stores temp data 
- variables in function 
- function header 
- small data 

**Static Data**:
- data that stays in memory for duration of program 

**Heap**:
- used for storing long-term data 
- programmer controls heap contents 
- much more space than stack 

# Memory Allocation: `malloc()`

```c
void *malloc(size_t size);
```
- allocates memory block size bytes long 
- return type void
- returns NULL pointer if fails to allocate 

### Where Does `malloc()` get Memory?

Manages private memory inside process
- when pool runs out of space, func asks kernel for more pages 
- kernel expands process's memory map:
	- `brk()/sbrk()` extends heap region 
	- `mmap()` creates anon memory mappings 

![[Screenshot 2025-11-03 at 16.01.30.png]]

### Memory De-Allocation: `free()`

Takes generic pointer to block of memory and returns for reuse 
- if memory `malloc()`d and not `free()`d then have **memory leak**
- can be dangerous, uses up available memory 

# `calloc()`

Allocates memory block of $n$ elements each of size bytes 
- useful to ensure old data not reused inappropriately 
- return type is void 
- returns NULL pointer if fails to allocate memory 

# `realloc()`

Allows dynamic change in size of previously allocated block of memory pointed to by `ptr`
- moves and copies contents needs to, frees original block which can change `ptr`
- returns NULL pointer if fails 

# `atoi()`

Converts string pointed to by `s` to an integer 
- other forms: `atof()`, `atol()`, `atoll()`

# The `->` Operator 

Gives shorthand accessing members of structures using pointer 

```c
struct point {
	int x;
	int y;
} pt, *ptr;

ptr=&pt;
```

Can become:
```c
pt.x=3;
(*ptr).x=3;
ptr->x=3;
```

