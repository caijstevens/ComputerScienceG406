#cs 

### MIPS

**M**icroprocessor without **I**nterlocked **P**ipeline **S**tages

Design principles:
- Simplicity = regularity
- Make common case fast
- Smaller = faster
- Good design needs good compromises

32-bit **RISC** processor:
- 32-bit words
- ~110 instructions in set
- 32 general purpose registers 

### MIPS Assembly
![[Screenshot 2025-05-04 at 19.12.10.png]]

Instruction types:
- **R-type**: register operands
- **I-type**: immediate operand
- **J-type**: for jumping

### R-type Instruction Format
![[Screenshot 2025-05-04 at 19.14.46.png]]

3 register operands:
- $rs, rt$: source registers
- $rd$: destination register

Other fields:
- $op$: the **opcode**, always 0 for R-type
- $funct$: **function**, second part of opcode. If first 6 bits of instruction are 0, known to be R-type. Function specifies which R-type instruction.
- $shamt$: **shift amount** for shift instructions, otherwise 0.


> [!done] Example
> Assembly code for adding values in registers 17 and 18, putting answer in register 16: $$add\space $s0, $s1, $s2$$ is translated to machine language:![[Screenshot 2025-05-04 at 19.20.07.png]]
> 
> 
> 

### I-type Instruction Format
![[Screenshot 2025-05-04 at 19.23.25.png]]

3 operands:
- $rs, rt$: register operands
- $imm$: 16-bit immediate written in two's complement
- $rs$ and $imm$ are source operands, $rt$ is source in some, destination in other

Other field:
- $op$: **opcode** completely determines instruction.


> [!check] Example
> Assembly code for adding number 5 to value of register 17, putting answer in register 16:$$addi\space $s0,$s1,5$$ is translated to machine language:![[Screenshot 2025-05-04 at 19.27.01.png]]

### J-type Instruction Format
![[Screenshot 2025-05-04 at 19.28.10.png]]
- $addr$: 26-bit address operand
- $op$: instruction completely determined by **opcode**.
- used for jump instructions such as $j$.

