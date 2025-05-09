#cs 
### Transistors

Before transistors:
- gears (babbage)
- relays/vacuum tubes (early electrics)

**Transistor** is electrically controlled switch
- turns on/off by voltage

Digital circuits constructed from circuits called **logic gates**
- logic gates perform boolean logic function
- logic gate created from 1+ transistors
![[Screenshot 2025-05-02 at 09.54.09.png]]
(g=gate, d=drain, s=source)
- if electricity flowing, nMOS closed, pMOS open

### Truth Tables

**AND:**

| A   | B   | Y   |
| --- | --- | --- |
| 0   | 0   | 0   |
| 0   | 1   | 0   |
| 1   | 0   | 0   |
| 1   | 1   | 1   |
![[Screenshot 2025-05-02 at 10.07.20.png]]

**OR:**

| A   | B   | Y   |
| --- | --- | --- |
| 0   | 0   | 0   |
| 0   | 1   | 1   |
| 1   | 0   | 1   |
| 1   | 1   | 1   |
 ![[Screenshot 2025-05-02 at 10.07.39.png]]

**XOR:**

| A   | B   | Y   |
| --- | --- | --- |
| 0   | 0   | 0   |
| 0   | 1   | 1   |
| 1   | 0   | 1   |
| 1   | 1   | 0   |
![[Screenshot 2025-05-02 at 10.07.51.png]]

**NOT:**

| A   | Y   |
| --- | --- |
| 0   | 1   |
| 1   | 0   |
![[Screenshot 2025-05-02 at 10.08.02.png]]

**NOR:**

| A   | B   | Y   |
| --- | --- | --- |
| 0   | 0   | 1   |
| 0   | 1   | 0   |
| 1   | 0   | 0   |
| 1   | 1   | 0   |
![[Screenshot 2025-05-02 at 10.08.56.png]]

### Transistors to Gates

**NOT:**
![[Screenshot 2025-05-02 at 10.13.34.png]]
- if $A$ **high**, then P1 is off and N1 is on, so $Y$ is connected to $GND$, and is therefore **low**.
- if $A$ **low**, then P1 is on and N1 is off, so $Y$ is connected to $V_{DD}$, therefore **high**.![[Screenshot 2025-05-02 at 10.16.12.png]]

**NAND:**
![[Screenshot 2025-05-02 at 10.17.13.png]]
- when $A$ is **low** and $B$ is **high**, then $A$ being **low** causes $P1$ to be **on** and $N1$ to be **off**. $B$ being **high** causes $P2$ to be **off** and $N2$ to be on. This means $Y$ is connected to $V_{DD}$ and is therefore **high**.![[Screenshot 2025-05-02 at 10.35.30.png]]

**AND:**
Essentially a combination of a NAND and a NOT gate![[Screenshot 2025-05-02 at 10.36.06.png]]
### Supply Voltage and Logic Levels

Chips do not deal in 0s and 1s.
- **voltages** are continuous values $0 \leq V \leq 5$.
- typically $0V = 0$ and $5V=1$ but need to tolerate **noise**.

**Low** voltage (ground/GND) is $0V$.
- **high** voltage historically $5V$ but just labelled $V_{DD}$ if unspecified.
- mapping of continuous voltage to discrete 0 or 1 is decided by defining **logic levels**.![[Screenshot 2025-05-02 at 10.52.31.png]]
- permitted range for high output: $V_{OH}$ to $V_{DD}$
- permitted range for low output: $GND$ to $V_{OL}$
- acceptable range for high input: $V_{IH}$ to $V_{DD}$
- acceptable range for low input: $GND$ to $V_{IL}$

Noise margins:
- $NM_H = V_{OH} - V_{IH}$
- $NM_L = V_{IL} - V_{OL}$

### The Static Discipline


> [!info] Rule
> If inputs meet **valid input thresholds**, then the system guarantees outputs will meet **valid output thresholds**.

- gates are grouped into **logic families**: gates of same family obey static discipline when used with co-family gates.
- therefore can apply digital abstraction and combine elements without concern over logic levels or analogue values.
![[Screenshot 2025-05-02 at 10.58.17.png]]

### Moore's Law

> [!info] Theorem
> Transistor density doubles in 2 years. Computer processing power doubles every 18 months.

