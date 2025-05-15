#cs 

### Entity-Relationship (ER) Modelling

**Conceptual** database design
- model for communication
- non-ambiguous but non-technical
- **Unified Modelling Language** (UML)

Structure:
- **entities** with **attributes**
- **relationships** between entities
- **constraints**
- not identical to RDM
- top-down approach
![[Screenshot 2025-05-15 at 22.40.05.png]]


| Entity-Relationship (ER) Modelling             | Relational Data Model          |
| ---------------------------------------------- | ------------------------------ |
| Object-based model                             | Record-based model             |
| Visual representation                          | Mathematically sound           |
| Used to understand\formulate data requirements | Used to define database schema |
| High-level, non-technical                      | Low-level, technical           |
| **Intuitive to work with**                     | **Not very intuitive**         |
![[Screenshot 2025-05-15 at 22.42.49.png]]

### Entities and Relationships

> [!info] Definition
> An **entity** is a "thing" requiring explicit representation
- visually represented as labelled rectangle 
- **entity (type)**: class of all objects with same properties
- **entity (occurrence)**: concrete instance of entity type

> [!info] Definition
> A **relationship** is a named association between multiple entity types
- visually represented as labelled line 
- there are constraints on number of entity occurrences able to participate in relationship

### Constraints, Cardinality and Participation

**Constraints** are most commonly a range
- $\min\dots\max$ or e.g. $0,1- 5,10\dots$
- $*$ means no constraint aka infinity

**Cardinality** (maximum):
- one-to-one $(1:1) \rightarrow$ "is head of"
- one-to-many $(1:*) \rightarrow$ "gives"
- many-to-many $(*:*) \rightarrow$ "attends"

**Participation** (minimum on opposite end):
- optional $(0) \rightarrow$ "giving a course" is optional for a teacher
- mandatory $(\geq 1) \rightarrow$ "attending a course" is mandatory for a student

### Attributes 

**Properties** of an entity type
- attribute **domain**: allowable values
![[Screenshot 2025-05-15 at 22.54.01.png]]
- primary key underlined

Attributes are either **simple** or **composite**:
- **simple**: only a single component
- **composite**: multiple components 
	- components indented

Attributes are either **single-valued** or **multi-valued**:
- **single-valued**: only one value for each occurrence
- **multi-valued**: multiple values for each occurrence
	- range of allowable number of values $[\min\dots\max]$

Attributes can be **derived**:
- computed from other attributes (prefixed with /)

### ER Model to RDM

**Logical** database design
- not always direct correspondence entity $\leftrightarrow$ relation\table
- use **foreign keys** as references for relationships
- $(1:1)$ relationship: decide based on **participation**
- $(1:*)$ relationship: decide based on **cardinality**

For many-to-many $(*:*)$ relationships:
- create **separate relation** with two foreign keys
- in ER model:
	- introduce new entity
	- connect with two $(1:*)$ relationships
	- old constraints to new entity
	- old entities get $1\dots 1$ constraints

### ER Model Construction Method

> [!success] Method
> 1. Identify entities and relationships from scenario
> 2. Draw rough ER diagram
> 3. Add constraints (min/max, participation/cardinality)
> 4. resolve $(*:*)$ relationships
> 5. add attributes, define primary keys
> 6. check if correct
- usually iterative process
