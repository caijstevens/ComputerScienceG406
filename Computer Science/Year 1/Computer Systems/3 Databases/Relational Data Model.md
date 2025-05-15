 #cs 

### Relational Data Model 

**Data Definition Language** too low-level
- need more abstract data model to describe structure
- mathematically sound

**Relational Data Model**:
- uses **mathematical relations**
- relations stored in tables 
- attributes values of a concrete instance of entity are related because they belong to same instance.

**Schema** of relation $R: R(A_1,A_2,...,A_n)$
- attributes $A_1, A_2,\dots, A_n$
- e.g. `Student(studentNo, prename, surname)`
- attribute order does not matter, names used

All data in database stored in **relations**.

### Terminology


> [!info] Definition
> **Relation**: table (with rows and columns)
- logical structure only
- can also be called "table" or "file"

> [!info] Definition
> **Attribute**: named column in a table, has a unique name 
- can also be called "column" or "field"

> [!info] Definition
> **Tuple**: a row in the table that holds specific values for all attributes
- can also be called "row" or "record"

> [!info] Definition
> **Domain**: set of allowed attribute values

> [!info] Definition
> **Cell**: value of specific attribute in a tuple
- intersection of row and column

> [!info] Definition
> **Degree**: number of attributes
- number of elements in a tuple/columns

> [!info] Definition
> **Cardinality**: number of tuples
- number of tuples/rows

> [!info] Definition
> A relation is **normalised** if it is appropriately structured e.g.
> 1. fulfils certain conditions
> 2. every cell has exactly one value
> 3. no repetition of identical tuples

> [!info] Definition
> **Relational Database**: a collection of normalised relations
- each relation has unique name

### Domain of an Attribute

Every attribute defined on a **domain**:
- defines meaning and allowed values
- can be distinct or same for different attributes
- correct operations can be permitted and incorrect ones avoided

### NULL

> [!info] Definition
> **NULL** indicates the **absence of a value**
- represents attribute value either currently unknown or not applicable.
- not normal value, not equal to False or "" (empty string), must be handled differently
- breaks two-valued logic, can cause issues

### Keys 

> [!info] Definition
> **Key**: set of attributes whose values uniquely determine a tuple

>[!info] Definition
>**Candidate key**: minimal set of attributes that is a key
- minimal: cannot drop any attribute 
- not: smallest possible number of attributes

>[!info] Definition
> **Primary key**: one candidate key selected to identify tuples

>[!info] Definition
> **Alternate key**: candidate key that is not primary key

>[!info] Definition
> **Simple key**: key that consists of single attribute 

>[!info] Definition
> **Composite key**: key that consists of multiple attributes

**Foreign keys** are used to reference other entities
- an attribute in relation $A$ that either matches the **primary key** of another table $B$ or is NULL.

### Integrity Constraints

**Domain constraints** for attributes
- values must lie in domain

**Entity integrity**:
- primary key attributes not NULL 
- guarantees each key has unique ID
- ensures foreign key values properly reference 

**Referential integrity**:
- foreign keys must match some primary key or be NULL 
- ensures valid references
- prevents tuple deletion if referenced elsewhere

### Views

**Views** are a different type of relation to earlier base relations.
- **virtual** (not stored physically)
- **derived** from base relation(s)
- **computed upon request** by user

Uses:
- show **customised information** to each user (can hide some info)
- compute/calculate **dynamic quantities** (e.g. age from birthday)

Views can be **updated** when:
1. only involve **single base relation**
2. contain either **primary key** or a **candidate key** of the base relation
3. do not use **aggregation** or **grouping** operations

### RDM Alternatives

**Network Data Model**:
- record-based data model (like RDM)
- records/tuples are nodes in a graph
- relationships (foreign keys) are edges
![[Screenshot 2025-05-15 at 22.23.27.png]]

**Hierarchal Data Model:**
- restricted network data model
- each node has **one parent** (but multiple children)
- represented as **tree**
![[Screenshot 2025-05-15 at 22.24.31.png]]

