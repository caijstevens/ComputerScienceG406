#pp 

# Structures `struct`

Collections of variables forming new data structure 
- elements of structure don't have to have same type 
- members of structure have names, specify to select 
- in some languages, structures and members are records and fields 

# Structure and Scope 

```c
struct point {
	int x;
	int y;
};
```
- each structure represents new scope
- names declared in scope don't conflict 

# Operations on Structures 

The `.` used to access a structure member is C operator 
- takes precedence over nearly all other operators including `*`

Assignment:
- `point2 = point1;`
- copies point1 into point2 in terms of $x$, then $y$ etc
- structures must have compatible types

Structures can contain structures

# Unions 

**Union** consists of members of possibly different types 
- compiler allocates enough space for largest members, overlay each other
- if **struct** contains int and double, memory is enough for int **and** double
- if **union** contains int and double, memory for union is space for **only a double**
- assigning new value to one member alters values of other members 

### Properties 

Structure and union differ in one way:
- members of structure stored at different memory addresses 
- union members stored at same address 

Members of union accessed in same way as members of structure:
```c
u.i = 82;
u.d = 74.8;
```

### Initialising Unions 

```c
union {
	int i;
	double d;
} u = {0};
```
- designated initialisers can also be used with unions 
- can save space in structures 

Enumerations used to mark which member of union was last to be assigned
- in number structure, can make 'kind' member `enum` instead of `int`

Structs can be passed by value into a function

### Creating New Types 

`typedef` can be used to assign names to types
```c
typedef unsigned char byte;
byte b1 = 12;
```
- can be used with structs and unions

# I/O in C

Methods:
- terminal 
- files
- arguments 

### Terminal 

```c
printf("%[flags][width][.precision][length]specifier" );
```
- write to `stdout` and read from `stdin`

Reads from terminal:
```c
int scanf ( const char * format, ...)
```
- format is same as above 

### File

- can use commands `fopen`, `fclose`, `fread`, `fwrite`

### Arguments 

```c
int main(int argc, char** argv){
	// argc: number of args 
	// argv: contains args
	if(argc > 1){
		printf("The first argument: %s", argv[1]);
		// first arg is argv[1] not 0
		// argv[0] contains program path
	}
	return 0;
}
```
