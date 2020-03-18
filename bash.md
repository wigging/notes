# Bash

Just some basic notes about writing and executing Bash scripts on a Mac.

Comments in Bash begin with the "#" symbol.

```bash
# comments go here
```

File extension of a Bash script is ".sh". To run the script in the terminal use the "bash" command. For the script to run, place the following line at the top:

```bash
#!/usr/bin/env bash
```

Declare variables by assigning a value to a reference. Bash variables have no data type so they can contain a number, string, or character. The variable is retrieved with the "$"" symbol.

```bash
name="Bart Simpson"
echo "My name is $name"
```

Test operators can be used in a Bash script to determine if a file or directory exists. A table of Bash test operators for files is available at [tldp.org](http://tldp.org/LDP/abs/html/refcards.html). The example below demonstrates whether a file named bash-test-file.md exists in the Desktop directory.

```bash
if [ -e ~/Desktop/bash-test-file.md ]
then
  echo "file exists"
else
  echo "file does not exist"
fi
```

This example determines whether a directory (folder) named pressure2 exists in the Desktop directory.

```bash
if [ -d ~/Desktop/pressure2 ]
then
  echo "folder exists"
else
  echo "folder does not exist"
fi
```
