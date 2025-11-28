 #nas 

Defines who can perform what actions 
- first computers were single-user, single-task 
- networked systems allowed large user numbers 

>[!tip] Basic Model 
>Subject wants to access resource for particular action.
>Corresponding request submitted to reference monitor. 
>Reference monitor accepts or rejects request based on access control policy.
- main operations are read/write/execute 

# Access Control Workflow 

Access request: subject, resource, action 
- PEP: Policy Enforcement Point (reference monitor)
- PDP: Policy Decision Point 
- Decision: permit/deny/not applicable
![[Screenshot 2025-10-27 at 12.13.27.png]]

A request is a triple $(s,o,a)$ and is granted if $a$ belongs to access matrix entry corresponding to subject $s$ and object $o$.
![[Screenshot 2025-10-27 at 12.14.23.png]]

# Access Control Lists 

Objects have associated list of subjects and access rights.![[Screenshot 2025-10-27 at 12.15.02.png]]
# Capabilities List 

Subjects provided with capabilities list showing access rights on given objects. (equiv to rows of matrix)
![[Screenshot 2025-10-27 at 12.15.39.png]]

# Intermediate Controls 

Introducing layers between subjects and objects to make policies more manageable 
- e.g. subject groups, role abstraction, security levels etc

### Groups 

Subjects with similar access rights placed in groups
- file associated with single group
- permissions associated with groups, not users 
![[Screenshot 2025-10-27 at 12.17.06.png]]

### Role Based 

$U$: set of users
$S$: set of sessions
$R$: set of roles
$P$: set of permissions

$UA(u)$: roles assigned to user $u$
$PA(r)$: permissions assigned to role $r$

User $u$ starts session $s$ and activates roles in $UA(user(s))$
- session $s$ can perform permission $p$ iff exists role $r$ activated by $s$ such that $p\in PA(r)$

Should use **least privilege**: only activate what you need

Extensions:
- **Role hierarchy**: role can be more senior than other, inherits permissions of junior role 
- **Separation of duty**: two given roles cannot be activated simultaneously
- **Binding of duty**: two roles either activated together or not at all
- **Administrative RBAC**: some roles can assign/revoke other roles to users 

# Bell-LaPadula Model 

Focuses on confidentiality of information 
- tuple $(S,O,A,L)$
	- $S$ is set of subjects
	- $O$ is set of objects 
	- $A$ = {execute, read, write} is set of access operations 
	- $L$ is lattice of security levels with partial ordering 

Confidentiality levels:
- unclassified $<$ confidential $<$ secret $<$ top secret 
Need-to-know categories:
- e.g. NATO, air, sea etc 

Subject clearance and object classification is a confidentiality level and a subset of categories ![[Screenshot 2025-10-27 at 12.23.20.png]]
Users can only read down.
![[Screenshot 2025-10-27 at 12.23.48.png]]
- but info can flow down

Users can only write up
![[Screenshot 2025-10-27 at 12.24.14.png]]

# Relationship-Based AC 

Authorisation graph has all subject-object relationships
- policy can check if path exists in graph
![[Screenshot 2025-10-27 at 12.24.54.png]]

# Chinese Wall Model 

**Subjects**: active entities accessing protected objects 

**Objects**: data organised in 3 levels:
- information
- dataset
- conflict-of-interest classes 

**Access rules**:
- read rule
- write rule
![[Screenshot 2025-10-27 at 12.26.03.png]]

Subject can read object if either condition satisfied:
- object in same dataset as object already accessed by subject 
- object belongs to conflict-of-interest from which subject has not yet accessed any information 
![[Screenshot 2025-10-27 at 12.27.05.png]]

Subject can write object if both conditions satisfied:
- subject can read object 
- no object can be read from different company dataset to one which write access is requested

This would mean that if subject reads objects from two different companies, it can **never** write 
- exceptions for sanitised info 

