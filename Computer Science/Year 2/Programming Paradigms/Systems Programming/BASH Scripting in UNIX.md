 #pp 

# Text Operations 

`sort`:
- sorts a file from `stdin`
- puts results in `stdout` or file with `-o filename`
- can redirect output to file with `>` and from file with `<`

`tr` (translate):
- `tr SET1 SET2` translates or deletes characters from `SET1` to `SET2`
- e.g. `tr 'A-Z' 'a-z'` makes lowercase version of `stdin`
- option `-c` takes complement of `SET1`
- option `-s` squeezes repeats to single character
- option `-d` deletes all characters in `SET1`
- e.g. `tr -dc '[:print:]'` deletes all non-printable characters

`uniq`
- remove or report repeated lines
- can be used with `sort` to find repeated lines
- e.g. `sort | uniq`
- use `-c` option to count number of repetitions

# File Handling

Files stored in hierarchical structure, allows grouping
- `ls` - list contents of current folder
- `cd` - change folder
- `mkdir` - make new folder
- `mv` - move a file/folder
- `cp` - copy a file/folder
- `rm` - delete file or with `-r` a directory
- `du` - how much space does a folder/file take
- `find` - list all files

Each file has three types of permissions:
- Read (r): Allows viewing the contents of the file
- Write (w): Allows modifying the contents of the file
- Execute (x): Allows running the file as a program

Permission groups:
- Owner: The user who owns the file
- Group: Other users in the file's group
- Others: All other users

Permission representation:
- represented as string of 10 characters (e.g `-rwxr-xr--`)
- first character indicates file type (`-` for file, `d` for directory)
- next three characters are owner's permissions (e.g `rwx`)
- following three characters are owner's permissions (e.g `r-x`)
- final three characters are others' permissions (e.g `r--`)

Changing permissions:
- use `chmod` to change file permissions
- syntax: `chmod [permissions] [file]`

# Shell Scripts 

Can write shell scripts in text editors
- saved with `.sh` extension
- begin with line `#!/bin/bash`

Running shell scripts:
- check/change permissions: `chmod a+x myscript.sh`
- at command line, type `./scriptname` and script should run

### For Loops 

```
#!/bin/bash
for f in *
do
	# something in here
	echo $f
done
```

### Parameters 

You can add parameters to script when you run them
- `./myscript.sh foo bar`
- refer to them using $ sign in scripts 

### If Statement 

```
#!/bin/bash
if [ $1 -lt $2 ]
then
	echo "yes" $1 "is less than" $2
else
	echo "no it isn't"
fi
```
- use `==,!=,-gt,-lt,-le,-ge`

### Environment Variables 

Store info about user session and are shared with programs started from shell ![[Screenshot 2025-10-13 at 14.31.29.png]]
### Extras 

`if [ -e FILE ]` - true if `FILE` exists
`if [ -z STRING ]` - true if `STRING` is empty

Variables:
- `VAR="Hello World"`
- `echo $VAR`
- `TD="The time is 'date'"`
- `echo $TD`
- output: The time is Mon 09 Oct 13:44:14 GMT 2023
