#cs 

### Compiling, Assembling and Loading


> [!info] Definitions
> **Compiler** translates high-level code into assembly language.
> 
> **Assembler** turns assembly code into machine language code (object file).
> 
> **Linker** combines object file with other machine language code
> 
> **Loader** puts executable into memory.

![[Screenshot 2025-05-05 at 16.09.01.png]]

Assembler makes two passes through assembly code, turns into object file.
- first pass: assembler assigns instruction addresses and finds all symbols and makes symbol table
- second pass: generates object file, linker creates executable by combining object file with other machine code, loader puts executable into memory and execution can start.

### Functions


> [!info] Definition
> Functions are pieces of code which can be accessed from other parts of the program.

- makes code more modular and readable
- MIPS assembly functions have inputs (**arguments**) and and output (**return value**).
- need agreement on how to call and return from function, and access input arguments and return value

**Call and return**:
```
               # caller function "main"
0x00400200     main:   jal   simple
0x00400204             ...

			   # callee function "simple"
0x00401020     simple: jr    $ra
```

Function `main` calls function `simple` using the `jal` instruction.
- `jal simple` (jump and link) jumps to address 0x00401020 (as j would) but also stores in $ra address where program returns after `simple` executed (here, 0x00400204)
- `jr $ra` (jump register) jumps to address stored in register. But `jr` is R-type, not J-type.

**Arguments and return value**:
```
main: li   $a0, 10     # argument 0 gets the value 10  
	  li   $a1, 5      # argument 1 gets the value 5  
	  li   $a2, 20     # argument 2 has value 20  
	  li   $a3, 10     # argument 3 has value 10  
	  jal  diffofsums  # call the function  
	  move $s0, $v0.   # put return value to $s0
	  ...  
	  
diffofsums:  
	  add  $t0, $a0, $a1   # sum of the first two arguments  
	  add  $t1, $a2, $a3   # sum of the other two arguments  
	  sub  $t2, $t0, $t1   # difference of the two sums  
	  move  $v0, $t2       # put return value at $v0 
	  jr   $ra             # return to caller
```
- `move` is another pseudo-instruction like `li`. Copies register value into another register. Implemented as:
```
add $s0, $v0, $0
```
- according to MIPS conventions on caller and callee behaviour:
	- caller places arguments into registers $a0 - $a3
	- return value placed into registers $v0 - $v1
	- saved registers $s0 - $s7 not modified by callee
- instead of directly conforming to convention, callee can first save important registers in **stack** and restore them before returning to caller.

### Loops

```
		# Initialize registers  
		li    $t0,   10          # load the value of N  
		li    $t1,   0           # initialize the counter (i)  
		li    $t2,   0           # initialize sum  
		
		# Main loop body  
loop:   addi  $t1,   $t1,   1    # i = i + 1 (increment the counter)  
		add   $t2,   $t2,   $t1  # sum = sum + i  
		beq   $t0,   $t1,   exit # if i = N, break from the loop  
		j     loop  
		
exit:   ...  
		...
```
- main loop implemented through unconditional jump instruction $j$ and branch instruction $beq$ which branches out of loop when values in registers $t0 $t1 become equal.

### Input/Output

```
# Get n from user and save  
li      $v0,   5      # load the syscall code 5 to $v0  
syscall               # read integer (syscall code is 5)  
move    $t0,   $v0    # syscall result (returned in $v0) moves to $t0
```
- get value of $n$ from user rather than hard-coding
- `syscall` instruction suspends program execution to provide OS-like service such as input, output or termination.
- type of syscall service specified by code stored in $v0.![[Screenshot 2025-05-05 at 16.37.08.png]]
Output and exit:
- after exiting main loop, print output and stop execution
```
exit:   # Print sum  
		li     $v0,   1    # print_string syscall code = 1  
		move   $a0,   $t2  
		syscall  
		
		# Exit  
		li     $v0,   10   # exit  
		syscall
```
- must declare end of program, otherwise computer will fetch next stored word and behaviour is unpredictable.