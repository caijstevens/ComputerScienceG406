#cs

### Relational Calculus and Algebra

Relations are **sets of elements**
- element is **tuple of attribute values**
- row in table = **one element** of set

Relational calculus (**declarative**):
- **set theoretic expressions** (predicate calculus / first order logic)
- **defines** new set based on existing ones

Relational Algebra (**procedural**):
- uses **operators to construct** new set from existing ones

Relational Calculus and Algebra are **equivalent languages**:
- used to define/create same sets
- for every calculus expression there is at least one algebraic expression 

Relational Calculus and Algebra are **not user-friendly**
- formal basis for comparing querying languages

Modern query languages:
- **relationally complete**: can produce same relations as algebra/calculus
- have **additional operations** (e.g. summing, grouping, ordering)
- **not Turing complete** (like general programming languages are)

### Relational Calculus

**Predicate**: a function that returns true/false when arguments given.
**Proposition**: the expression obtained when replacing values for arguments of a predicate

Let $P(x)$ and $Q(x)$ be two predicates with argument $x$. Then:
- the "set of all $x$ such that both $P(x)$ **and** $Q(x)$ are true" is: $$\{x|P(x)\land Q(x)\}$$
- the "set of all $x$ such that $P(x)$ **or** $Q(x)$ are true" is: $$\{x|P(x) \lor Q(x)\}$$
- the "set of all $x$ such that $P(x)$ is **not** true" is: $$\{x|\sim P(x)\}$$
### Tuple Relational Calculus

Variable values are **tuples**
- use predicate to specify tuple should be in a relation, e.g. `Staff(s)`
- use `s.name` for named element in tuple $s$
- use **quantifiers** for more complex predicates:
	- **existential** $\exists$ "there exists"
	- **universal** $\forall$ "for all"

Example: "all tuples $s$ of the relation Staff with attribute salary > 10000"$$\{s|\text{Staff}(s)\land s.\text{salary} > 10000\}$$
### Domain Relational Calculus

Variable values are **attribute values**

### Relational Algebra

**Procedural:** specifies operations to construct new set from existing ones

Basic operations:

| Unary                | Binary                       |
| -------------------- | ---------------------------- |
| Selection ($\sigma$) | Union ($\cup$)               |
| Projection ($\pi$)   | Set Difference ($-$)         |
| Rename ($\varrho$)   | Cartesian product ($\times$) |
Derived operations:
- Intersection ($\cap$)
- Division ($\div$)
- Join ($\bowtie$ natural join, equi-join, theta join, outer join, semi-join)

### Selection 

$\sigma_{condition}(R)$
- unary operation (single relation)
- **selects** subset of tuples/rows from $R$ that satisfy the specified condition
- SQL: `SELECT * FROM R WHERE <condition>`

### Projection

$\Pi_{col1, col2, ...}(R)$
- unary operation (single relation)
- **selects** specified subset of attributes/columns from $R$
- **eliminates duplicates**
- corresponding SQL: `SELECT DISTINCT col1, col2 [, ...] FROM R`

### Combining Selection and Projection

Can combine operations
- outer operation applied to result of inner operation

### Union

$A\cup B$
- binary operation (two relations)
- **selects** tuples in $A$ **or** $B$
- **"adds up"** tuples from both relations
- **eliminates duplicates**
- SQL: `SELECT... UNION[ALL] SELECT...`

### Set Difference 

$A - B$
- binary operation (two relations)
- **selects** tuples in $A$ but **not in** $B$
- **removes** tuples from copy of $A$ that are also in $B$
- SQL: `SELECT... { MINUS | EXCEPT } SELECT...`

### Intersection

$A\cap B$
- binary operation (two relations)
- **selects** tuples in $A$ **and** in $B$
- SQL: `SELECT... INSERSECT SELECT...`

### Union Compatibility 

Computing $A\cup B$ or $A-B$ or $A\cap B$
- schemata of $A$ and $B$ must match
	- same number of attributes
	- matching attributes must have same domain
	- attributes names are ignored
- $A$ and $B$ then called **union compatible**

If relation has additional attributes:
- use **projection** to create union-compatible relations
![[Screenshot 2025-05-17 at 18.32.23.png]]

### Cartesian Product 

$A\times B$
- binary operation (two relations)
- generates **all possible combinations** of tuples in $A$ and $B$ by concatenating
- results in $r_{A}\times r_{B}$ tuples with $c_{A} + c_{B}$ attributes 
- no compatibility requirements on $A$ and $B$
- attributes with same name prefixed with relation name 
- SQL: `SELECT * FROM A,B` or `SELECT * FROM A CROSS JOIN B`

Usually only interested in specific combinations
- SQL: `SELECT * FROM A CROSS JOIN B WHERE <criterion>` or `SELECT * FROM A JOIN B ON <criterion>`

### Rename

Algebraic expressions can be very complex
- **decompose** into smaller operations
- give names to intermediate expressions for reuse
- can use **assignment** operation: `Name <-- <expression>`
- but creates multiple expressions

Rename operation:
- $\rho_Y(X)$ returns $X$ renamed as $Y$
- $\rho_{Y(A,B,C,...)}(X)$ returns $X$ renamed as $Y$, with attributes renamed as $A,B,C,...$
- useful when reusing same relation in different roles

![[Screenshot 2025-05-17 at 18.39.40.png]]

### Division 

$A\div B$
- binary operation (two relations)
- only keep tuples from $A$ that exist in all possible combinations with $B$
![[Screenshot 2025-05-17 at 18.42.00.png]]
- $B$ has a subset of attributes from $A: \space A(X_1,X_2,\dots,Y_1,Y_2,\dots)$ and $B(Y_1,Y_2,\dots)$
- find **all possible combinations**
- only keep **tuples and attributes** that are in $A$
	- find combinations not in $A$
	- project to attributes only in $A$
	- **remove** from $A$
![[Screenshot 2025-05-17 at 18.44.02.png]]

### Joins 
![[Screenshot 2025-05-17 at 18.47.21.png]]
$A$ [INNER] JOIN $B$ ON $\text{<criterion>}$
- condition = $A\bowtie_{attr1=attr2} B$
- **Theta** join ($\theta$-join): for general criterion $\theta$
- **Equijoin**: some equality criterion
- **Natural join**: equijoin over all common attributes
- **Semijoin**: inner join and project to attributes of left relation
![[Screenshot 2025-05-17 at 18.47.34.png]]

$A$ LEFT [OUTER] JOIN $B$ ON $\text{<criterion>}$
![[Screenshot 2025-05-17 at 18.48.23.png]]

$A$ RIGHT [OUTER] JOIN $B$ ON $\text{<criterion>}$
![[Screenshot 2025-05-17 at 18.48.30.png]]

$A$ FULL [OUTER] JOIN $B$ ON $\text{<criterion>}$![[Screenshot 2025-05-17 at 18.48.42.png]]
