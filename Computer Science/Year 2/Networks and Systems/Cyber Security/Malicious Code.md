#nas 

# Malicious Code Execution 

System provides set of atomic actions (open file, send message)
- actions can be composed together to create **trace** (calculator, email application)
- security policies define which traces are secure
- **malicious code execution** is the execution of a trace which is possible, but not secure

### Closed System 

A closed system has a **predetermined** set of possible traces

### Open System 

All actions are **enabled by default** but non secure traces are detected at runtime and avoided

![[Screenshot 2025-10-13 at 11.26.12.png]]

### Reference Monitor 
![[Screenshot 2025-10-13 at 11.26.44.png]]
- reference monitor is in charge to check the traces in an open system
- should be **NEAT**:
	- **Non-bypassable**: not possible for subject to access resource without submitting request to monitor
	- **Evaluable**: monitor should be simple enough and specified well enough that behaviour can be understood
	- **Always-invoked**: every submitted request should be evaluated
	- **Tamperproof**: not possible to modify monitor

# Malicious Code: Steps 

Malicious code execution is execution of non-secure trace
- only possible in open systems
- locate or insert malicious behaviour in system
- find a way to jump from normal secure system to malicious code

Malicious code execution only possible when reference monitor not **NEAT**
- might be by-passed or not invoked, allowing jump
- might not have been evaluated, may contain flaws
- might have been tampered with

### Methods 

**Reverse Engineering**:
- deconstruct system and modify it, therefore opening a closed system
- understand how product works based on final product
- if code executed remotely, might be harder to change, but if executed locally, might require decompiler
- routes for reverse engineering as attacker:
	- find flaw in function check so input always checks condition
	- modify condition/check so test becomes true
	- jump directly to execution by passing check

**Code Injection**:
- modify control flow 
- shell code/SQL/XSS (Cross site scripting)
	- **XSS** is modifying the webpage on client-side by injecting content within original server content. User cannot differentiate authentic and injected code.
	- **SQL** injection: SQL queries take input data from web forms e.g. `SELECT COUNT(*) FROM 'users' where user='$u' and password = '$p'`. If user inputs empty string for password and `'or '1' = '1' --` then query becomes `SELECT COUNT(*) FROM 'users' where user = ''or '1' = '1'--' and password = ''`. Everything after `--` is ignored query returns all users, meaning count greater than 1, therefore granting access without having actual password.

# Malware Taxonomy 

**Virus**:
- code that can replicate itself usually through human intervention
**Worm**:
- code that can replicate itself between devices usually without human intervention
**Trojan**:
- pretends to be normal application so that users download and install
**Rootkit**:
- gain remote access and controls device as root
**Botnet**:
- bot is a machine controlled by attacker. Bots become part of botnets, a number of computers controlled by attacker
**Adware**: 
- advertising-supported malware designed to deliver advertisement to users spontaneously
**Spyware**:
- monitors user activities without consent, e.g collecting key logs, screen watching
**Ransomware**:
- encrypt computer resources until victim pays ransom
**Backdoors**:
- sets grounds for other malware by opening backdoor onto device
**Key-loggers**:
- records everything user types on system, gather login details and send to key-logging program

# Prevention

**Input sanitisation**:
- ensure that input content cannot escape its scope
- check for SQL/JavaScript/Python scripts in files or forms
**Close the system**:
- remove features that can be potentially misused, confine dangerous subsystems
- use static website, prevent installation of new programs
**Analyse input**:
- allow only input leading to secure behaviour
- **signature matching**: search for known patterns of bad code, usable but can miss new attacks
- **anomaly detection**: normal behaviour recorded, deviations flagged. Can catch new attacks but false positive common
**Confine code execution**:
- malicious code only executed at level of privileges of executing agent
- run programs as normal user, run executable search queries on server with read-only capabilities. But attack still happens and privileges can be escalated.