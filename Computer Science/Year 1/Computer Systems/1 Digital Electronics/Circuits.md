#cs 

### Key Circuits

**Combinatorial/combinational circuits:**
- **Adders**: add contents of two registers
- **Decoders**: decodes $n$-digit binary number into $2^n$ data lines
- **Multiplexors**: use binary number to select input

**Sequential circuits:**
- **Latches/flip-flops**: basic memory element

### Adders and Half-Adders

**Half-Adders:**
- inputs: $A, B$
- outputs: sum, carry![[Screenshot 2025-05-04 at 17.18.47.png]]
> [!error] Half-Adder Rules
> | Without Carry | With Carry |
> | --- | --- |
> | $0+0=0$ | Carry $+0+0=1$ |
> | $0+1=1$ | Carry $+0+1=0$ with Carry |
> | $1+0=1$ | Carry $+1+0=0$ with Carry |
> | $1+1=0$ with Carry | Carry $+1+1=1$ with Carry |

**Adders:**
- inputs: $A, B$ and the **carry** from the previous bit
- use **two** half-adders: add $A$ and $B$ first, then add in carried bit:
![[Screenshot 2025-05-04 at 17.29.55.png]]
- full adders can be chained together to increase bit-adders by powers of 2: **"ripple carry adder**.![[Screenshot 2025-05-04 at 17.38.25.png]]
### Subtractor

Can create **twos-complement negative** by inverting bits and adding 1
- subtract $b$ from $a$ by adding $-b$.![[Screenshot 2025-05-04 at 17.39.22.png]]
- implement NOT gates and set $C_{in}=1$ to convert $b$ to $-b$.

### Decoder

Decoder has $N$ inputs and $2^N$ outputs. 
- asserts one output depending on binary number represented by $N$ input bits.
- outputs called "one-hot" because one output is "hot" (high) at a given time
![[Screenshot 2025-05-04 at 17.41.12.png]]
![[Screenshot 2025-05-04 at 17.41.58.png]]

### Mux (Multiplexor)

Chooses 1 of many inputs to steer to single output under direction of control inputs.
- if input can come from several places, Mux can funnel multiple sources to single input.
- has $k+2^k$ inputs and $1$ output. First $k$ inputs represent binary number (selector $S$), output takes value of one of remaining $2^k$ inputs, the one indexed by selector.
![[Screenshot 2025-05-04 at 18.06.51.png]]![[Screenshot 2025-05-04 at 18.06.59.png]]![[Screenshot 2025-05-04 at 18.07.08.png]]
### Tristates

Normal buffer has either 0 or 1 at output.
- **tristate** buffer can be electrically disconnected from bus wire.
![[Screenshot 2025-05-04 at 18.15.47.png]]
- **floating** means not connected to source, therefore output neither 0 nor 1

**Inverting Tristate**:
![[Screenshot 2025-05-04 at 18.16.45.png]]

**Tristates** can help create larger multiplexors:
![[Screenshot 2025-05-04 at 18.20.26.png]]

![[Screenshot 2025-05-04 at 18.20.36.png]]

### Simple ALU
![[Screenshot 2025-05-04 at 18.30.07.png]]
