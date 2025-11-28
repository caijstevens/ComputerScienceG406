#pp 
# x++ or ++x

`x++` means `x=x+1`, `++x` means `x=x+1`
- `x++` returns the value of `x` first, then increments
- `++x` increments first, then returns value of `x`

# `switch` Statements

```c
switch ( expression ){
	case const-expr: statements
	case const-expr: statements
	default: statements 
}
```
- if no `break` statement, execution falls through
- continues to execute case blocks even after case found

# Variables 

Basic data objects manipulated by program
- **declarations**: declare variables used, type and initial value
- **expressions**: combine variables/constants to form new values 

# Data Types 

Every variable must have type
- char: single byte to store character (-128 to 127)
- short: integer type for small whole numbers (2 bytes, -32768 to +32767)
- int: integer type, whole numbers (4 bytes, -2147483648 to +2147483647)
- long int, long long int: integer type, large or very large whole numbers
- float: single precision floating point number
- double, long double: double precision floating point number

# `signed` vs `unsigned`

- signed/unsigned applies to char or integer types
- unsigned integers are always positive or 0
	- signed char (8 bits)
	- unsigned char (8 bits)
- `<limits.h>` and `<float.h>` specify limits for given system
- system and architecture dependent

Unsigned arithmetic is modulo $2^n$
- signed overflow undefined/implementation-defined

# Character Constants 

These are integer values that are written as character in single quotes
- e.g. '0' = 48 in ASCII 

Can also include escape characters:
- `\n` newline character
- `\a` alert (bell) character
- `\t` horizontal tab 
- `\0` NULL character

# String Constants 

Zero or more characters in double quotes
- array of chars that has a NULL character at the end of the string
![[Screenshot 2025-10-20 at 16.31.06.png]]

# Enumerations 

Values of variables that have a small number of possible values.
- each value has a name (an **enumeration** constant)
```c
enum suit{CLUBS, DIAMONDS, HEARTS, SPADES};
```
- names of constants different from other identifiers
- enumeration constants similar to `#define` directive constants
- if enumeration declared inside function, constants not visible outside function

# Functions 

```c
int power( int base, int n ) {
	int p;
	for ( p = 1; n>0; n-- )
		p = p * base;
	return p
}
```

