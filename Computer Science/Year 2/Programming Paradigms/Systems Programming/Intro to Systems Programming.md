#pp 
Involves development of individual pieces of software that allows system to function as single unit
- incl. operating systems, game engines etc

# C / C++

Provides low-level access to memory
- simple set of keywords
- efficient and flexible
- C++ provides more advanced techniques

# Simple Programs 

![[Screenshot 2025-10-06 at 14.32.52.png]]
- saved in `.c` file extension

### Pre-processor Directives 

Lines that start with `#` are commands to C pre-processor
- e.g. `#include <stdio.h>`
- looks for source code file `stdio.h` and includes before compilation, file required to use standard input and output library

### `main()` Function Declaration

All C programs have `main()` function. Called by runtime system to start program running.
- only one can exist

### `printf()` Function Call 

Function call to `printf()` implements formatted text to console window
- string arg includes escape sequence `\n` which generates newline char 

### `return` Statement 

UNIX programs often return zero value to indicate normal exit 
- no return statement, no problem
- wrong type return value may cause warning or problem at run-time

### Temperature Converter

![[Screenshot 2025-10-06 at 14.37.46.png]]
- code fragment converts temp from F to C and prints result
- could change variable `C` to a double (stores float but would have to change output format)

### `printf()`

First parameter explains how rest formatted
![[Screenshot 2025-10-06 at 14.39.43.png]]

# Compiling 

![[Screenshot 2025-10-06 at 14.40.15.png]]
### C Pre-processor

Directives handled by pre-processor, edits C programs just prior to compilation
- system header files use `#include <stdio.h>`
- if `< >` used, `/usr/include` prioritised by convention
- if `" "` used, current working directory prioritised

User header files use `#include "fibonacci.h"`
- searches current directory first then system directories

# Definitions (Macro)

Used to provide definitions in code
```C
#define MY_AGE 18
...
int nextBirthday = MY_AGE + 1;
```

# Conditionals

```C
#ifdef A_NAME // tests if A_NAME is #defined
	<program text>
#else
	<program text>
#endif
```
- `#ifndef` is "if not defined"

### Using Macros

![[Screenshot 2025-10-06 at 14.51.58.png]]
Using parameterised macro instead of actual function has advantages:
- program slightly faster: function call requires overhead but macro invocation does not
- macros "generic": can accept args of any type if resulting program valid

Potential disadvantages:
- args aren't type-checked, unexpected results possible
- work as direct substitutions in code, should always use brackets