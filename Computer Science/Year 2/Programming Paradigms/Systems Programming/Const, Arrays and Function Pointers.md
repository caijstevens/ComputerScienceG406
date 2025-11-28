#pp 

# `const`

Keyword in C to define variables whose values should not change after initialisation
- prevents accidental changes 
- code more predictable and maintainable 

Promotes **safety, optimisation and readability**

Uses:
- constants 
- array sizes 
- function parameters 

```c
const int get_fixed_value() {
	return 42;
}
```

Different when pointers involved.
- `const int *ptr_a` and `int const *ptr_a` are equivalent 
- but `int const *ptr_a` and `int *const ptr_b` are different 
- in first, pointer is `ptr_a` and it cannot be changed 
- in second, pointer is `const`, so ptr_b can b changed but pointer itself cannot be.

# Arrays 

Can have multi-dimensional arrays 
```c
int arr3d[3][2][4] = {
	{{1, 2, 3, 4}, {5, 6, 7, 8}},
	{{9, 10, 11, 12}, {13, 14, 15, 16}},
	{{17, 18, 19, 20}, {21, 22, 23, 24}}
};
```

# Setting Data 

### Memset 

```c
void *memset(void *ptr, int value, size_t n);
```
- fills the first $n$ bytes of memory at ptr with byte value 

Use cases:
- zero-initialising arrays 
- clearing sensitive data before freeing memory 
- resetting large regions of contiguous memory quickly 

# Copying Data 

### Memcpy 

```c
void *memcpy(void *dest, const void *src, size_t n);
```
- copies $n$ bytes from src to dest 
- operates on **raw memory**

# Other Memory Functions 

```c
memcmp(const void *a, const void *b, size_t n);
```
- compares first $n$ bytes of two memory blocks 

```c
memchr(const void *ptr, int value, size_t n);
```
- scans memory for first occurrence of byte value 
- useful for binary search within raw buffers 

```c
alligned_alloc(size_t alignment, size_t size);
```
- allocates memory aligned to a given power of 2 boundary 

# Function Pointers 

Functions decay to pointers when names used 
- to find address of `strcpy`, can just use `strcpy` or `&strcpy`

Syntax for declaring variables whose type is function pointer:
- ordinary function declaration:
  ```c
	char *strcpy(char *dst, const char *src);
	```
- can now have function pointer:
  ```c
	char *(*strcpy_ptr)(char *dst, const char *src);
	```
- parentheses separate return type * from pointer variable *
- pointer to pointer to function has ** inside:
  ```c
	char *(**strcpy_ptr_ptr)(char *, const char *) = &strcpy_ptr	
	```
- too many pointers confusing; use `typedef`s instead 


