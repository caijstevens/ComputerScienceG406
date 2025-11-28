 #pp 

An identifier in a V program is visible only in a portion of the source code called its **scope**

# Storage Classes 

Storage class defines scope and lifetime of variables/functions 

### Extern 

When variable defined, allocated storage 
- when declared, compiler knows variable of given type exists 
- top-level vars default to extern 
- lifetime and scope of whole program 

### Static 

Mutually exclusive to extern 
- static vars have same lifetime as program 
- static **global** has file scope
- static **local** has function scope 
- static var inside function keeps value between invocations 

### Auto 

Vars have same lifetime as function where defined 
- have function scope and function lifetime 
- local vars auto by default 

### Register 

Suggests that var should be stored in register, not main memory 
- cannot use address of (&) operator on register vars 
- storing in register much faster to access 
- not all register variables declared as such 
- register is quite rare 

# Call Stack 

Divided into **stack frames**
- each frame is data associated with one call to one func and contains func's args, local vars and execution address ![[Screenshot 2025-11-03 at 17.40.11.png]]
# Function Parameters 

Have same properties of local variables 
- auto storage duration and block scope 
- each param initialised when function called 

# Global Variable Pros and Cons

Pros:
- global vars convenient when many funcs share var or when few funcs share large number of vars

Cons:
- changing global var during maintenance requires checking each function in same file 
- if global var assigned incorrect value, may be difficult to identify guilty function 
- functions that rely on global variables hard to reuse elsewhere