#nas 

# System 

### Components of a System 
- **Subject**: has an **identity** and some **capabilities**
- **Resource**: has an **identity** and some **properties**
- **System**: **connects** entities and has a **purpose**
- **Action**: **interaction** between subjects and resources 

### CIA Triad 

Three main security properties:
- **Confidentiality**: outcomes of actions in system only visible by authorised subjects
- **Integrity**: actions modifying system can only be performed by authorised subjects
- **Availability**: subjects can perform all actions they are authorised for

# Threats, Vulnerabilities, Attacks

>[!info] Definition 
>A **vulnerability** is a flaw in the system that makes it possible for a threat to occur.
>- Can be hardware, software, human-based 

>[!info] Definition 
>An **exploit** is a concrete way of taking advantage of a vulnerability

>[!info] Definition 
>A **threat** is a way of causing damage to a system.

>[!info] Definition 
>An **attack** on a system is the realisation of a **threat** through the **exploitation** of one or more **vulnerabilities**.

# Vulnerability Lifecycle

![[Screenshot 2025-10-06 at 12.12.21.png]]
**Black Risk**: Only discovery group aware
**Grey Risk**: Public is aware, but no patch is available
**White Risk**: Public should patch their system
**Zero Day Exploit**: Exploit available at time of disclosure

# STRIDE Model 
Used by Microsoft

Classification of threats
- **Spoofing**: using someone else's credentials to perform an operation
	- Failure of identification/authentication
- **Tampering**: malicious modification of data
	- Failure of integrity 
- **Repudiation**: denying having performed an operation
	- Failure of Accountability/Identification
- **Information disclosure**: exposure of information to unauthorised users
	- Failure of confidentiality
- **Denial of service**: denying access to service to legitimate users
	- Failure of availability
- **Elevation of privilege**: unprivileged user gains privileged accesses
	- Failure of confinement/authentication

Disadvantages of STRIDE:
- not **exhaustive**: not every threat falls into specific category
- not **exclusive**: some threats fall in multiple categories