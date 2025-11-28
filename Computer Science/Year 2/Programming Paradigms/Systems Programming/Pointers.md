#pp 

# Pointer Variable 

>[!info] Variable 
>A logical name for an allocated area of memory, assigned to store a value 

`int i=10`
- value of `i` is 10
- memory address of `i` is `&i`, value 4

>[!info] Pointer Variable 
>Stores a memory address.
>
>```c
>int *p;
>p=&i;
>```
- now pointer variable p stores memory address of variable i

```c
printf("%d %d\n", i, *p) ;
```
- output: "10 10"
- indirection operator `*` means "value at"

# Pointer Operations 

Use `*` to access and modify value:
```c
*p = 7; // assign value of 7 to i
*p = *p + 1; // add 1 to value of i
```

>[!warning] Warning 
>Applying indirection operator to uninitialised pointer causes undefined behaviour:
>```c
>int *p;
>printf("%d", *p); /*** WRONG ***/
>```
>Assigning a value to `*p` is particularly dangerous:
>```c
>int *p;
>*p = 1; /*** DANGEROUS ***/
>```

# Pointer Assignment 

C allows the use of assignment operator to copy pointers of same type
```c
int i, j, *p, *q
p = &i;
q = p;
```
![[Screenshot 2025-10-27 at 14.06.44.png]]
- any number of pointer variables may point to same object

# Pointers as Arguments 

We can try writing `swap()` function but not very good.
- by passing pointer to variable instead of variable value, `swap()` can be fixed

Want to write function to swap int variable values:
```c
void swap(int a, int b) {
	int temp;
	temp = a;
	a = b;
	b = temp;
}
```
- have to pass in `&x` and `&y` though 

# Strings 

Strings represented as array of characters
```c
char a[] = "Hello worlds";
char b[13];
b = a; // Not allowed
char *c;
c = a; // Allowed 
```
- sets pointer c to same address as a
- assignment of array to array not possible in C
- instead use `strcpy(b,a)`
	- first arg is destination `#include <string.h>`

# Pointer Arithmetic 

```c
int a[10];
int *pa;
pa = &a[0];
pa = a;
```

If write `a[x]`, works by adding x to a to find pointer
- therefore `a[x]` == `*(a+x)`

# Peeking at Memory 

Can look at bits of memory
- find adjacent local variables and parameters 

Can have pointers to pointers:
```c
int i, *p, **q;
p = &i;
q = &p;
```
