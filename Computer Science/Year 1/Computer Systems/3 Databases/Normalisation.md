#cs 

### Normalisation


> [!success] Multi-Step Process
> 1. 1st Normal Form (1NF)
> 2. 2nd Normal Form (2NF)
> 3. 3rd Normal Form (3NF)
> 4. Boyce-Codd Normal Form (BCNF)
> 5. 4th Normal Form (4NF)
> 6. 5th Normal Form (5NF)

### 1st Normal Form (1NF): No Repeating Groups 

Table is in **1st Normal Form** if:
- it has **no repeating groups**
- each cell has one value
- repeating group means attribute with multiple values for single primary key occurrence

If there is fixed number of repetitions, can use **separate attributes**
![[Screenshot 2025-05-16 at 12.52.29.png]]

Two general solutions:
1. **Flattening**: fill empty cells with repeating values
2. **Separate relation**: create separation relation by linking with primary/foreign keys

### 2nd Normal Form (2NF): No Partial Dependencies

Table is in **2nd Normal Form** if:
- it is in 1NF
- **no partial functional dependencies**: every non-key attribute dependent on whole primary key
- only relevant for relations with **composite keys**

Solution:
- **remove** partially dependent attributes
- place in **new relation** along with copy of determinant
![[Screenshot 2025-05-16 at 13.13.48.png]]

### 3rd Normal Form (3NF): No Transitive Dependencies

Table is in **3rd Normal Form** if:
- it is in 2NF
- has **no transitive functional dependencies**

Solution:
- **remove** transitively dependent attributes
- place in **new relation** along with copy of determinant
![[Screenshot 2025-05-16 at 13.16.49.png]]

### Overall Solution 
![[Screenshot 2025-05-16 at 13.18.24.png]]
