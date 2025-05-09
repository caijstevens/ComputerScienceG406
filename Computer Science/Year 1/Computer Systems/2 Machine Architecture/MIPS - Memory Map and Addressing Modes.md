#cs 

### MIPS Memory Map

**word**: 32-bits (in MIPS, high level architectural choice)
**byte**: 8-bits (always)

MIPS uses 32-bit memory addresses, memory is **byte addressable**.![[Screenshot 2025-05-04 at 19.40.21.png]]
MIPS address space spans $$2^{32}\space\text{bytes}=4\space\text{gigabytes (GB)}$$
Word addresses divisible by 4 (two LSBs always 0)
- range from $0$ to $0xFFFFFFFC$

MIPS architecture divides address space into 4 parts:
- **text** segment
- **global data** segment
- **dynamic data** segment
- **reserved** segments

**Text segment** stores machine language program.
- 256MB of storable code.
- four MSBs of word address in text segment all 0 (and two LSBs)
- 26 bits of $addr$ field of $j$ instruction suffice to specify address of any instruction stored in text segment

**Global data segment** stores global variables (can be seen by all functions in program).
- 64kB of storable data.
- accessed using pointer $gp
- initialise $gp at middle of GD segment at value 0x10008000. value stays constant throughout execution, global variables addressed as offsets from 0x10008000.

**Dynamic data segment** stores data dynamically allocated and deallocated throughout program execution.
- largest segment of memory used by program, almost 2GB of address space.
- data stored in **stack** and **heap**

**Reserved segments** used by operating system, cannot directly be used by program.

### MIPS Addressing Modes

Addressing mode types:

| Reading and writing operands | Writing the Program Counter |
| ---------------------------- | --------------------------- |
| Register Only                | PC-Relative                 |
| Immediate                    | Pseudo-direct               |
| Base Addressing              |                             |
**Register Only**:
- registers for all source and dest operands
- R-type instructions use Register only

**Immediate**:
- registers and 16-bit immediate as operands
- some I-types use Immediate

**Base addressing**:
- used in memory access instructions
- I-type instructions
- memory operand address computed by adding base address in $rs$ to 16-bit offset stored in $imm$.
- instructions:
	
| code | use        |
| ---- | ---------- |
| $lw$ | load word  |
| $lb$ | load byte  |
| $sw$ | store word |
| $sb$ | store byte |
Base addressing example:
```
lw $s0, 0($0)    # read data word 0 and load it into $s0
sw $s3, 4($0)    # write $s3 to data Word 1
sw $s4, 0x20($0) # write $s4 to data Word 8
				 # Notice use of hex in imm, supported by MIPS assembly
sw $s5, 200($0)  # write $s5 to data Word 50
```
![[Screenshot 2025-05-05 at 15.58.38.png]]![[Screenshot 2025-05-05 at 15.58.48.png]]
**PC-relative addressing**:
- branch instructions use PC-relative to specify new program counter value if branch taken
- branching instruction is I-type ![[Screenshot 2025-05-05 at 16.01.09.png]]
**Pseudo-direct**:
- in **direct addressing**, address specified in instruction
- MIPS does not support direct
- uses pseudo-direct in J-type instructions
- calculates new value of PC called **Jump Target Address** (JTA)
	- two LSBs left as 0
	- next 26 bits taken from $addr$ field of J-type
	- four MSBs left to 0
![[Screenshot 2025-05-05 at 16.04.05.png]]
- in MIPS microprocessor, $j$ instruction just copies 26 bits of $addr$ field over to 26 bits of PC.