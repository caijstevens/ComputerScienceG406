#pp 

# Compiling 

`gcc -o outfile file.c`
- use `-o` to name output
- use `-E` option to do pre-processing only
- use `-S` to go as far as compilation only
- use `-c` to go as far as assembly only
- use `-l` to link e.g. external libraries

# Makefiles 

Need rule-set when compiling numerous files together
- `make`
- rule-file required, Makefile
- declarative programming set of rules

```MakefileFormat
target [target ...]: [component ...]
		[command 1]
		...
		[command n]
```
- target: what you want to make
- component: something that needs to exist

![[Screenshot 2025-10-20 at 14.43.23.png]]

### Macros 

Can be used to store definitions
- `CC=gcc`

Can be generated from commands
- `DATE=date`

### Pattern Rules 

Can specify pattern rule matching multiple files
- contains one `%` in target
- matches any non-empty substring 
- e.g. `%.c` matches any file ending in `.c`

### Automatic Variables 

Variables with values computed for each rule executed based on target 
- substring matching % is called **stem**

- `$@`: file name of rule target
- `$<`: name of first prerequisite
- `$?`: name of all prerequisites newer than target 
- `$^`: names of all prerequisites, each only listed once
- `$*`: stem with which implicit rule matches
	- if target is `dir.a` and target pattern is `%.a` then stem is `dir`

# Beyond Make 

Makefiles bad for large projects
- cannot automate everything or find external libraries

### Autotools

Simplifies portability across systems with simple rules instead of Makefiles
- not very simple
- best for Linux
- used by lots of open-source software

### CMake

Cross-platform tools, control compilation using compiler independent configuration files, generate own native makefiles
- flexible
- best for Linux or MacOS
- not always intuitive 

# Statements in C

A **statement** is a single instruction:
`printf("Hello world!\n");`

**Compound statement** is set of statements
```c
{
printf("Hello ");
printf("world!\n");
}
```

### Iteration Statements 

While:
```c
while ( expression ) {
	statement
};
```

Do:
```c
do {
	statement
} while ( expression );
```

For:
```c
for ( expr1 ; expr2 ; expr3 ){
	statement
};
```
- expr1 = initialisation
- expr2 = conditional 
- expr3 = increment 

`break` causes innermost loop to be exited immediately

`continue` causes next iteration for loop to begin
- in case of while or do loop, test part executed immediately
- for loop, control first passes to increment steps

`if-else` 
- `if` allows choice between two alternatives by testing expression 
- `if` statement may have `else` clause 
```c
if ( expr1 ) {
	statement1
} else {
	statement2
}
```
