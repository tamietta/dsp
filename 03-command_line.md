# Learn command line

Please follow and complete the free online [Bash Scripting Tutorial](https://ryanstutorials.net/bash-scripting-tutorial/) or [Codecademy's Learn the Command Line](https://www.codecademy.com/learn/learn-the-command-line). These are helpful tutorials. You should be able to go through these in a couple of hours.

**Note:** Bash is not installed on a PC. Rather, PC users must install Cygwin. Once Cygwin has been installed, the command line interface witll _emulate_ bash. You can find all information regarding Cygwin [here](https://www.cygwin.com/).

---

### Q1.  Cheat Sheet of Commands  

Here's a list of items with which you should be familiar:  
* show current working directory path
* creating a directory
* deleting a directory
* creating a file using `touch` command
* deleting a file
* renaming a file
* listing hidden files
* copying a file from one directory to another

Make a cheat sheet for yourself: a list of at least **ten** commands and what they do.  (Use the 8 items above and add a couple of your own.)  

| Command            | Function                                            |
| --------------     | --------------------------------------------        |
| `pwd`              | show current working directory path                 |
| `mkdir <dir>`      | creating a directory                                |
| `rm -r <dir>`      | deleting a directory and its contents               |
| `touch <file>`     | creating a file using `touch` command               |
| `rm <file>`        | deleting a file                                     |
| `mv <old-name> <new-name> ` | renaming a file                            |
| `ls -a <path/to/dir>`       | listing hidden files                       |
| `cp <original-path/to/file> <new-path/to/file>` | copying a file from one directory to another |
| `echo <text> > <file>`      | write \<text\> to file                     |
| `grep '<pattern>' <file>`   | output lines containing \<patter\> to file |
| `man <command>`   | show documentation for command                       |

---

### Q2.  List Files in Unix   

What do the following commands do:  
`ls`  
`ls -a`  
`ls -l`  
`ls -lh`  
`ls -lah`  
`ls -t`  
`ls -Glp`  

| Command            | Function                                         |
| --------------     | --------------------------------------------     |
| `ls`               | List all files/directories in current directory  |
| `ls -a`            | List all hidden and non-hidden files/directories |
| `ls -l      `      | List in long format                              |
| `ls -lh`           | List in long format with file-size units         |
| `ls -lah`          | List hidden/non-hidden in long format with file-size units |
| `ls -t `           | List sorted by time modified                     |
| `ls -Glp`          | List with colours, in long format, with '/' after directories   |

---

### Q3.  More List Files in Unix  

Explore these other [ls options](http://www.techonthenet.com/unix/basic/ls.php) and pick 5 of your favorites:

1. `ls -a` - hidden files
2. `ls -p` - append '/' to directories
3. `ls -l` - long format
4. `ls -R` - recursive subdirectories
5. `ls -t` - order by last modified

---

### Q4.  Xargs   

What does `xargs` do? Give an example of how to use it.

Takes a string from STDIN, and converts it to space-separated arguments to the given command.

**Example**

```bash
find . -name "*.pyc" | xargs rm -rf
```
 
The command above finds all files in the current directory with the extension, `.pyc`, pipes `|` the output as STDIN to `xargs` to convert as arguments to 'rm -rf'.