#cs 

### Functionally Complete Sets

> [!info] Definition
> A **functionally complete set** of Boolean operators is one which can be used to express all possible truth tables by combining set members into a Boolean expression.

Any logic circuit can be constructed with just **AND**, **OR** and **NOT**.
- **NOR** or **NAND** gates alone create a functionally complete set.

**NOR:**
- AND: $A \cdot B = \overline{(\overline{A + A}) + (\overline{B+B})}$
- OR: $A+B = \overline{(\overline{A+B}) + (\overline{A+B})}$
- NOT: $\overline{A} = \overline{A+A}$

**NAND:**
- AND: $A\cdot B = \overline{(\overline{A\cdot B}) \cdot (\overline{A\cdot B})}$
- OR: $A+B = \overline{(\overline{A\cdot A}) \cdot (\overline{B\cdot B})}$
- NOT: $\overline{A} = \overline{A\cdot A}$

### Digital Design Principles

**Abstraction:** hiding details when not important

**Discipline:** Restricting design choices to simplify modelling and design.

**Three -ys:**
- **Hierarchy:** dividing system into modules and submodules
- **Modularity:** well-defined functions and interfaces for modules
- **Regularity:** encouraging uniformity to enable module swapping or reuse.

### Circuits

> [!info] Definition
> A **circuit** is a network that processes discrete-valued variables.

A circuit has:
- 1+ discrete valued input terminals
- 1+ discrete valued output terminals
- specified relationship between inputs and outputs
- specified delay between inputs changing and outputs responding
![[Screenshot 2025-05-02 at 15.56.12.png]]

Circuit made up of **elements** and **nodes**.
- an **element** is a circuit with inputs, outputs and specs.
- a **node** is a wire joining elements; voltage conveys discrete valued variable![[Screenshot 2025-05-02 at 16.17.25.png]]
### Combinational Logic

> [!success] Combinational logic rules:
> 1. **Individual gates** are combinational circuits.
> 2. Every circuit **element** must be a combinational circuit.
> 3. Every node is either an **input** to the circuit or connecting to **exactly one output** of a circuit element.
> 4. The circuit has **no cyclic paths** - every path through the circuit visits any node at most once.

### Boolean Algebra

Used for specifying the function of a combinational circuit.
- to analyse and simplify circuits to give specified truth table

Variables represented by letters, $A,B,C$ etc.
- **complement/inverse** denoted as $\overline{A}$
- variable or complement is a **literal**

The **AND** of several literals is a **product** e.g. $A\overline{B} C$ or $A\overline{C}$
- can be written $A\cdot B\cdot C, ABC, A \cap B \cap C, A \land B\land C$
- **minterm** is product in which **all** function inputs appear once

the **OR** of several literals is a **sum** or **implicant** e.g. $A+B+C$ or $A+C$
- can be written $A+B+C, A\cup B\cup C$ or $A\lor B\lor C$
- a **maxterm** is a sum in which **all** inputs to function appear once each 

|                           | AND        | OR      |
| ------------------------- | ---------- | ------- |
| **notation**              | $A\cdot B$ | $A+B$   |
| **combination**           | product    | sum     |
| **once each combination** | minterm    | maxterm |

### Sum of Products

Every expression can be written as minterms ORd together: $$(A \cdot B\cdot C) + (A \cdot \overline{B} \cdot\overline{C}) + (\overline{A}\cdot B\cdot C)$$
![[Screenshot 2025-05-02 at 17.18.46.png]]
- every row can be represented by a minterm that is true
- OR together all of the rows with 1s
- SoP form of the above truth table: $$F(X,Y,Z) = \overline{X}\cdot\overline{Y}\cdot\overline{Z}\space + \overline{X}\cdot Y\cdot Z\space + X\cdot\overline{Y}\cdot Z\space + X\cdot Y\cdot\overline{Z}$$
### Product of Sums

Every expression can be written as maxterms ANDd together: $$(\overline{A}+\overline{B}+\overline{C})\space\cdot(\overline{A}+B+C)\space\cdot (A+\overline{B}+\overline{C})$$
![[Screenshot 2025-05-02 at 17.31.37.png]]
- every row can be represented by a maxterm that is false
- AND together all of the rows with 0s
- PoS form of the above truth table: $$F(X,Y,Z)=(X+Y+Z)\cdot(X+\overline{Y}+Z)\cdot(\overline{X}+Y+Z)\cdot(\overline{X}+\overline{Y}+\overline{Z})$$

### Boolean Algebra

Used to produce simplest equivalent expression to be turned into circuitry.


> [!success] Axioms of Boolean Algebra
> 
> | Number | Axiom | Number' | Dual Axiom | Name |
> | --- | --- | --- | --- | --- |
> | $A1$ | $B=0$ if $B\neq 1$ | $A1'$ | $B=1$ if $B\neq 0$ | Binary field |
> | $A2$ | $\overline{0}=1$ | $A2'$ | $\overline{1}=0$ | NOT |
> | $A3$ | $0\cdot 0=0$ | $A3'$ | $1+1=1$ | AND/OR |
> | $A4$ | $1\cdot 1 = 1$ | $A4'$ | $0+0=0$ | AND/OR |
> | $A5$ | $0\cdot 1=1\cdot 0=0$ | $A5'$ | $1+0=0+1=1$ | AND/OR |
- axioms cannot be proven; defined or assumed

> [!info] Theorems of One Variable
> 
> | Number | Theorem | Number' | Dual Theorem | Name |
> | --- | --- | --- | --- | --- |
> | $T1$ | $B\cdot 1 = B$ | $T1'$ | $B=1$ if $B +0=B$ | Identity |
> | $T2$ | $B\cdot 0=0$ | $T2'$ | $B+1=1$ | Null element |
> | $T3$ | $B\cdot B=B$ | $T3'$ | $B+B=B$ | Idempotency |
> | $T4$ | $\overline{\overline{B}}$ | - | - | Involution |
> | $T5$ | $B\cdot\overline{B}=0$ | $T5'$ | $B+\overline{B}=1$ | Complements |
- theorems can be proved by applying axioms and checking cases

> [!info] Theorems of Several Variables
> 
> | Number | Theorem | Dual Theorem | Name |
> | --- | --- | --- | --- |
> | $T6$ | $B\cdot C = C\cdot B$ | $B+C=C+B$ | Commutativity |
> | $T7$ | $(B\cdot C)\cdot D=B\cdot(C\cdot D)$ | $(B+C)+D=B+(C+D)$ | Associativity |
> | $T8$ | $B\cdot(C+D)=B\cdot C+B\cdot D$ | $(B+C)\cdot(B+D)=B+(C\cdot D)$ | Distributivity |
> | $T9$ | $B\cdot(B+C) = B$ | $B+(B\cdot C)=B$ | Covering |
> | $T10$ | $B\cdot C+B\cdot\overline{C}=B$ | $(B+C)\cdot(B+\overline{C})=B$ | Combining |
> | $T11$ | $B\cdot C+\overline{B}\cdot D+C\cdot D = B\cdot C+\overline{B}\cdot D$ | - | Consensus |
> | $T11'$ | $(B+C)\cdot(\overline{B}+D)\cdot(C+D) = (B+C)\cdot(\overline{B}+D)$ | - | - |
> | $T12$ | $\overline{B_0\cdot B_1\cdot B_2...} = \overline{B_0} + \overline{B_1} +\overline{B_2} ...$ | - | De Morgan's |
> | $T12'$ | $\overline{B_0 + B_1 + B_2...} = \overline{B_0} \cdot \overline{B_1} \cdot\overline{B_2} ...$ | - | - |


### De Morgan's Theorem

> [!info] Theorem
>$\overline{A\cdot B} = \overline{A}+\overline{B}$
>
