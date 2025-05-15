#cs 

### Databases

Advantages:
- flexible and complex queries
- data centrally stored and shared
- minimal data redundancy
- central access and control
- data structure explicitly defined
- data logically structured and related
- internal representation independent of external one

### Three-Level ANSI-SPARC Architecture

Internal-conceptual-external
- (basically like an API for a database)
- realises data abstraction
	- users access same data, customised views
	- users change views without affecting others
	- internal structure changed without affecting users

**External** level:
- user view
- multiple views of same data (e.g. date formats)
- adapted for needs
- different entities, attributes, relationships
- can be derived/calculated

**Conceptual** level:
- community view shared by all users
- describes what data stored in DB
	- entities, attributes, relationships
	- constraints, security info
- logical structure of DB that supports external views
- no storage-specific details

**Internal** level:
- physical representation of DB
- describes how data stored
- optimal runtime and storage use
- interface to OS
- compression/encryption
![[Screenshot 2025-05-15 at 21.18.57.png]]

DBMS mainly handles physical organisation
![[Screenshot 2025-05-15 at 21.26.20.png]]



### Database Schema and Instance

Database **Schema** (intension):
- complete DB description
- result of DB design process
- should not change afterwards
- multiple **external** schemata, one **conceptual** schema and one **internal** schema

| Schema Type | Contents                                    |
| ----------- | ------------------------------------------- |
| External    | Different views                             |
| Conceptual  | All entities/attributes/relationships       |
| Internal    | low-level description, storage, indexes etc |
Database **Instance** (extension/state):
- concrete data in DB at certain time
- changes at every data manipulation
- different instances can correspond to same schema

### Data Independence

![[Screenshot 2025-05-15 at 21.26.50.png]]

**Logical data independence**:
- external schemata remain same if logical structure changed on conceptual level.

**Physical data independence**:
- conceptual schema remains same if internal schema changed.

### Database Design

> [!info] Three phases:
> 1. Conceptual
> 2. Logical
> 3. Physical

**Conceptual**:
- construct first high-level model of data
	- ER modelling
	- entities, attributes, relationships, constraints
- use user's requirements spec
- independent of physical considerations
- relevant for conceptual and external level
- fundamental understanding of system

**Logical**:
- construct relational data model
- use conceptual design, map info to tables
- **normalisation** to eliminate redundancies and anomalies

**Physical**:
- describe implementation of logical design
- **storage, access, security**
- optimise performance
