#cs 

### Top-Down vs Bottom-Up Design 

**Top-down** approach: ER model
- start from data requirements
- graphical description of DB
- identify entities, attributes and relations 

**Bottom-up** approach: Normalisation
- start with actual data in tables
- analyse relationships
- re-design tables in "better" way
- (difficult for large DBs, requires formalisation)

 **"Better"** way:
 - **intuitively** - minimise required space and avoid anomalies
 - **no redundancy**
	 - wasteful for storage space
	 - can cause inconsistencies
	 - exception: **foreign keys**

Redundancy examples:
- **multi-valued attributes**: need to be stored in separate rows
- **dependencies** between attributes

Anomalies:
- **insertion anomaly**
	- new records need to duplicate existing data
	- cannot add partial records (because NULL primary key)
- **modification anomaly**
	- modifying only one value can cause inconsistencies
- **deletion anomaly**
	- losing other data when deleting one

### Decomposition

Method of avoiding anomalies
- adapt schema and decompose
- from: `Student(id, prename, surname, college, collegeAddress)`
- to: `Student(id, prename, surname, college)` and `College(college, collegeAddress)`

### Normalisation

Principles of how to decompose tables/relations
- depends on **functional dependencies** e.g `id` $\rightarrow$ `college` $\rightarrow$ `collegeAddress`

> [!info] Definition
> **Functional dependencies** describe the relationship among attributes in the same table/relation

- strongly affect data anomalies
- normalisation basis
- determine keys (candidate, primary, foreign)
- determine combinable attributes in new tables/relations.

> [!attention] Important
> If $A$ and $B$ are two **sets** of attributes in a relation, we say: $$\text{"}B \text{ is functionally dependent on } A\text{"} (A\rightarrow B)$$ or: $$\text{"}A\text{ functionally determines } B\text{"}$$ if each value of $A$ is associated with **exactly one** value of $B$.
- $A$ and $B$ are **sets**, so can consist of multiple attributes
- $A\rightarrow B$ basically means "if you know the value(s) of $A$ then you know the value(s) of $B$"
- $A$ is the **determinant** of $B$
- functional dependencies must hold **at all times, for all possible instances** of a relation

**Full** functional dependency:
- $B$ is functionally dependent on $A$
- $B$ is **not** functionally dependent on any proper subset of $A$

**Partial** functional dependency:
- $B$ is functionally dependent on $A$
- $B$ **remains** functionally dependent on at least one proper subset of $A$

**Transitive** functional dependency:
- if $A\rightarrow B$ and $B\rightarrow C$ then $C$ is **transitively dependent** on $A$ via $B$

### Closure of a Set of Dependencies

> [!info] Definition
> Given a set of functional dependencies $F$, its **closure** $F^{+}$ are all functional dependencies that are implied by the dependencies in $F$.
- need set of **inference rules** to compute $F^{+}$

> [!success] Armstrong's Axioms
> 1. **Reflexivity**: if $B\subseteq A$, then $A\rightarrow B$
> 2. **Augmentation**: if $A\rightarrow B$, then $A,C\rightarrow B,C$
> 3. **Transitivity**: if $A\rightarrow B$ and $B\rightarrow C$ then $A\rightarrow C$
- these inference rules are **complete** (all dependencies derivable) and **sound** (no extra wrong dependencies derivable)

Further rules (derived from Armstrong's):
4. **Decomposition**: if $A\rightarrow B,C$, then $A\rightarrow B$ and $A\rightarrow C$
5. **Union**: if $A\rightarrow B$ and $A\rightarrow C$, then $A\rightarrow B,C$
6. **Composition**: if $A\rightarrow B$ and $C\rightarrow D$, then $A,C\rightarrow B,D$

The **closure** $F^{+}$ of $F$ can be computed by:
1. starting with all dependencies in $F$
2. repeatedly applying Armstrong's axioms
3. add any new dependencies discovered

```COMPUTE_CLOSURE(F)

F+ = F
repeat
	for every functional dependency f in set F+
		apply rules of reflexivity and augmentation to f
		add new functional dependencies to set F+
	for each pair f1,f2 of functional dependencies in set F+
		if f1,f2 imply a functional dependency f3 using transitivity
			then add f3 to set F+
until set F+ does not change anymore
```

Example:
![[Screenshot 2025-05-15 at 23.43.30.png]]
