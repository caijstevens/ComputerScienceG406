 #pp 

# History of UNIX

Simpler and faster approach than MULTICS
- initial assembler implementation for PDP-7 and PDP-11
- rewritten in C in 1973
- first OS written in high-level portable language
- focuses on multiuser OS and high-end users

# The Shell 

Perform work on computer through text interface
- can run programs and control how they work
- move between different directories
- perform multiple commands to achieve more complex work
- many shell choices
![[Screenshot 2025-10-10 at 15.18.56.png]]

### Ethos of UNIX Shell 

Many small programs rather than one monolith
- allow user to combine programs together to make new functionality using **pipes** and **script files**

### Basic Commands 

| command name | description             |
| ------------ | ----------------------- |
| pwd          | print working directory |
| ls           | list contents           |
| man          | help manual             |
| cd           | change directory        |

### Pipes

Shell provides many small tools that can be combined
- pipes are a means to do this
- each command takes input and produces output

Can redirect input/output 
- `<` take input from file
- `>` write output to file
- `|` take output of command and use as input to next

![[Screenshot 2025-10-10 at 15.25.15.png]]

### `grep`

A search tool
- can search through files or results from running command 
- uses regular expressions for matching

# Regular Expressions 

Concise way to match different strings
- `.` matches any single character
- `*` matches any number of proceeding character
- `?` matches one of proceeding character
- `+` matches one or more of proceeding character
- `[ABC]` class as single character
- `[A-Z]` all upper case characters A to Z

# File Permissions in UNIX

Permission groups:
- owner - who created the file
- group - users in same group
- others - everyone else