# UNIX Slides #

### What is this repository for? ###

* Set of slides about UNIX operating systems
* Version: 0.1

# Introduction to UNIX

---
## Why UNIX?
* One of the most used operating systems nowadays
	* Very popular in the academic world, government agencies, and industry

* Different variants of UNIX, yet all of them share some basic features (conforming to several standards)
	* Hierarchical file system
	* Identical interfaces for data, devices and interprocess communication
	* Background processes and daemons
	* Synchronous and asynchronous processing
	* Standardized tools
	* High degree of portability

* Linux is based on Unix
	* Aims to conform to the various UNIX standard, but no Linux distribution is branded as UNIX
	* The main problems are time and expenses 
	* Its de facto near-conformance with UNIX standards, is what have enabled Linux success in the UNIX market

---
# A bit of UNIX history
* 1969: Development started by Ken Thompson at Bell Laboratories (AT&T corporation)
	* Written in assembly code for a digital PDP-7 computer
	* Some ideas taken from MULTICs (Multiplexed Information and Computing Service)
		* MULTICs is an earlier operating system (project collaboration between AT&T and MIT)
		* AT&T withdrew from MULTICs, frustrated at the failure to develop an economically viable and usable OS
		* Indeed Brian Kernigham (one of the fathers of the C programming language and also researcher at Bells labs at the time) called it UNICs (Uniplexed Information and Computing Service), name which derived later into UNIX

* 1970: Unix is rewritten in assembly language for another computer (the PDP11 back then a powerful machine)
	* Vestiges of this PDP-11 heritage can be found in various names still in used in most UNIX implementations, including Linux

---
# A bit of UNIX history
* A landmark we cannot omit in the UNIX history is the design and implementation of the C programming language by Dennis Ritchie and Kernigham

* 1973: The C language was mature to a point where UNIX kernel could be almost entirely written in C
	* UNIX became one of the earliest operating systems to be written in a high-level language
	* This fact made subsequent porting of UNIX to other hardware architectures possible
	* It also explains why C (also C++) have come to be used so widely as system programming languages today

---
# Unix Versions
* Between 1969 and 1979, UNIX went through a number of releases known as editions (each edition brought several milestones)

	* 1st Edition (November 1971): Run on PDP-11 and contained many programs used still today: ar, cat, chmod, cp, cd, ed, find, ln, ls, mail, mkdir, mv, rm, sh, su, and who	

	* 2nd Edition (June 1972): Installed on 10 machines within AT&T

	* 3rd Edition (February 1973): C compiler was included and provided the first implementation of pipes

	* 4th Edition (November 1973): Almost totally written in the C language

	* 5th Edition (June 1974): UNIX was installed on more than 50 systems

	* 6th Edition (May 1975): First edition widely used outside AT&T

---
# Inconveniences are sometimes very convenient
* Over that period of time, UNIX reputation began to spread within AT&T and beyond

* Problem: AT&T could not sell software at the time: it was sanctioned by the US government

* The provided solution is probably one of the most important ones in computer science history: at the beginning of 1974 AT&T allowed the use of UNIX within universities

---
# Two important variants (BSD and System V)
* January 1979 saw the release of the 7th edition of UNIX, which included a) improved reliability and file systems and b) a number of new tools: awk, make, sed, tar, uucp, the Bourne shell, and a Fortran compiler

* From this point UNIX derived into two important variants: BSD UNIX and System V

* To understand that divergence we need to go back to 1975/1976, when Thomson (the guy who wrote the first version of UNIX) spent a year as visiting professor at the University of California Berkeley
	* worked with several graduate students adding new features to UNIX such as the C shell, the vi editor, and improved file system, sendmail, a pascal compiler, and virtual memory management system
* Under the name of Berkeley Software Distribution (BSD) this version of UNIX, including its source code, came to be widely distributed
* In 1983, the computer research group at the University of California released the 4.2BSD version, which contained a significant amount of new code: a complete TCP/IP implementation, including sockets and other networking tools
	* This version became very popular among universities around the world


---
# Two important variants (BSD and System V)

* AT&T's ban was removed during mid-70's and the breakup became effective at the beginning of the 80's 
	* AT&T could then sell software products and commercialize UNIX

* System III was the first version sold by AT&T in 1981
	* Many developers were employed to develop applications and notably improve documentation

* System V developed in 1989 included many features from BSD (especially network facilities)

*  In addition to various BSD distributions spread through academia, by the end of the 80-s, UNIX was available in a range of commercial implementations on various hardware

* Contrary to proprietary operating systems, the high availability of UNIX distributions (compliant either with System V or BSD) made UNIX systems increasingly attractive from a commercial perspective due to portability of applications	

---
# UNIX Variants

1. UNIX BSD
2. UNIX System V
3. Solaris
4. Digital Ultrix
5. True64 UNIX by HP
6. IMG's AIX
7. Hewlett-Packard's (HP's) HP-UX
8. NeXT's NeXTStep
9. MAC OS (Apple)
	* iOS
10. Linux
	* Android OS

---
# UNIX Standards
* UNIX development was not controlled by a single vendor or organization
	* Many groups contributed to its evolution (AT&T, Berkeley, etc.)
	* Positive side: innovations
	* Negative side: implementations diverged over time, making difficult to write UNIX applications

* UNIX and C language standardization
	* Applications can be easily ported from one to another system when conforming to a given standard

* Standards usually made by independent groups
	* ISO C
	* POSIX
	* Single UNIX Specification

* UNIX implementations are referred to the two implementations standards defined by BSD and System V

---
# The UNIX Architecture
* Kernel 
	* Software controlling hardware resources and providing an environment for other programs to execute
* System calls
	* Interface with the Kernel
* Libraries
	* Functions build on top of the System Calls
	* Make easy to use kernel features
* Shell
	* Application providing an interface to other applications

![Unix Architecture](./unix.png)

---
# The UNIX shell
* Interface for every UNIX System
* A shell is an interpreter
	* Accepts a command
	* Interprets the command
	* Runs the command
	* Waits for the next command
* Commands have the following form: `command [options] [files]`
```bash
ls -l start1.txt star2.txt
cd tmp
pwd
```

---

# The man command
* `man`: shows information about how system calls, library functions, and other commands work
* Basic form: `man (keyword) [manual page]` 
* Examples of use
```bash
man ls
man time 3
man -k keyword
man man
```

* `man` paginates the output on the screen
	* `f` moves one page forward
	* `b` moves one page back
	* `G` goes to the end of the page
	* `xG` goes to the page x of the output
	* `/keyword` goes to appearances of the keyword on the output
	* `q` terminates the command 

* `apropos (keyword)`: searches man pages for a given keyword

---
# UNIX File System
* Hierarchical arrangement of files and irectories

* Everything stars in the root directory, denoted by `/`

* `/` is also used as separator to indicate the location of a file or directory

* Every entry in the file system is a file or a directory (or a link)

* Single entries can be referred either by 
	* absolute path (starting from the root) e.g., `/usr/sbin/bzip2`
	* relative paths (regarding the current directory) e.g.,  `../../jonh`

* Every file has associated three types of rights
	* read
	* write
	* execute

---
# UNIX Files
* File permissions are indicated with 9 bits

* The first 3 indicate the permissions for the owner of the file for reading, writing and executing

* The second group of 3 indicates the permissions for users of the same group as the owner

* The third group indicates the permissions for the rest of users

* These permissions are indicated with the letters `r`, `w`, and `x`

* `chmod`: changes permissions on a file

* `chown`: changes the owner of a file

---
# UNIX Files

![Unix Architecture](./file-info.png)

---
# UNIX commands related to the File System
* `pwd`: shows the current directory where the shell is
* `cd`: changes the directory where the shell is
```bash
cd \usr\bin #changes the directory to \usr\bin
cd ~ #changes the directory to home folder
cd - #changes to the previous directory
```
* `mkdir`: creates a new directory
```bash
mkdir lib #creates a directory called lib within the current directory
```
* `rmdir`: deletes an empty existing directory
* `ls`: lists the content of a directory
```bash
ls -l # lists the content showing detailed information about each file/folder
ls -F # lists the content indicating the type of each file (executable, regular file, folder)
```
* `file`: shows information about a file
```bash
file template.txt 
# template.tex: LaTeX 2e document, ASCII text
```

---
# Working with files
* `cat`: shows the whole content of a file
* `less` and `more`: shows content of a file page after page
* Editors
	* `kate`
	* `nano`
	* `vi`, `vi(m)`
	* `emacs`
* `echo`: prints something on the output
```bash
echo $home #prints the home directory
echo $OLDPWD #prints the previous directory if exist
echo hola #prints hola
```
* Every shell has acess to three files
	* standard input (`stdin`), from where the input is taken
	* standard output (`stdout`), where the output is put
	* standard error (`stderr`), where error messages are put

* `read`: reads from the input and assigns it to a variable
```bash
read a # waits for user to type something
```

---
# UNIX redirection
* Any command can put the output and error messages to another file or take the input from a different file
	* redirection
* UNIX provides the following redirection options
	* `<`, `>`, `2>` redirect input, output, and error
```bash
cat hola.txt > adios.txt #writes all the content of hola.txt into adios.txt
read a < hola.txt #reads a line from the file hola.txt and assign it to a
ls -l out5 2> /dev/null #if ls -l out5 produces an error, it will be written into the /dev/null file
```
	* `A|B` the output of the command `A` becomes the input of the command `B` 

---
# Copying, updating info, and removing files
* `cp`: copy a file or a directory
```bash
cp out3 out5 #copies the file out3 into out5
cp -r /juan/home backup #copies all the content of home into backup 
```
* `rm`: removes files or directories
```bash 
rm out5 # removes out5
rm -r Downloads # removes Download
rm -r # removes the content of the current directory
```
* `touch`: updates the access time and modification time of a file
```bash
touch out4 #change the access time of out4 (assumption: out4 exist)
touch out6 #creates a new  empty file out6, with access time equal to the current time
```

* `mv`: moves (rename) files or directories

---
# Options for command execution

* `cmd &`: executes `cmd` in background

* `cmd1 ; cmd2`: executes cmd1, then cmd2, etc.

* `{cmd1 ; cmd; }`: executes commands as group in the current shell

* `(cmd1 ; cmd; )`: executes commands as group in the current shell

* `cmd $(cmd2)`: Uses output of `cmd2` as input of `cmd1`

```bash
cmd1 `cmd2` #also performs command substitutions
```

* `cmd $((expression))`: idem as before, but it does an arithmetic substituion

* `cmd1 && cmd2`: executes `cdm2` only if `cmd1` has been sucessful

* `cmd1 || cmd2`: executes `cmd2` only if `cmd1` fails


---
# Options for command execution
```bash
# Execute sequentially
cd; ls

# All output is redirected
(date; who; pwd) > logfile

# Sort file, page output, then print
sort file | pr -3 | lp

# Edit files found by grep
vi `grep -l ifdef *.cpp`

# Specify a list of files to search
egrep '(yes|no)' `cat list`

# POSIX version of previous
egrep '(yes|no)' $(cat list)

# Print file if it contains the pattern
grep XX file && lp file

# Otherwise, echo an error message
grep XX file || echo "XX not found"
```

---
# Options for command execution
* `history`: shows a list of the commands executed associated with a number

* How to navigate the history?

	* `!!`: executes the last command showed by history

	* `!-n`: executes the n command in history starting from the last one

	* `!n`: executes the command number n in history

	* `<Ctrl>+r`: recursive search on the history

	* `!xt`: the last command that starts with xt


---
# Commands and wildcards

* UNIX commands can be used with wildcards
	* `?` one character
	* `*` 0 or more characters
	* `[ab]` any character included in the range
	* `{conf,loc}` conf and loc

```bash
#assume our folder contains the files out1,out2,out3, out4, progf, and prog.o
ls -l out* # detailed list of out1, out2, out3, and out4
ls -l [1-3] # detailed list of out1, out2, and out3
ls -l {1,3} # detailed list of out1, and out3
```

---

# Variables
* Bash allows declaring variables

* A variable consists of any number of letters, digits or underscores
	* case sensitive
	* cannot start with a digit
	
* A variable is assigned a value with the `=` operator
	* there may not be any whitespace between the variable name and the value

* A variable value can be accessed using the `$` operator

* By default, the shell treats variable values as strings, even if the value is a digit

* Bash allows creating integer variables using `declare -i`

```bash
var1=3+4
echo  $var1 #prints 3+4
declare -i var2
var2=3+4
echo $var2 #prints 7
```

---
# Built-in Variables
* Automatically set by the shell and can be used by any command

* `$#`: Number of command-line arguments

* `$-`: options currently in effect

* `$?`: exit value of the last executed command

* `$$`: process number of the shell

* `$0`: current command name

* `$n`: Individual arguments of the command line (e.g., `$1`, `$2`, ... `${10}`)

* `$*, $@`: All arguments in command line


---
# Calling the shell
* /bin/bash
	* Reads several configuration files `/etc/profile`, `~\.bash_login`, or `~\.profile`
	* Every nonlogin shell also reads `~\.bashrc`	
* /bin/sh
	* Reads $EVN instead of `~\.bashrc`

* Write commands in a file
	* First line on the file is the so-called sheban #!/bin/bash
	* Besides the file name, several arguments can be used
	* Arguments will be executed one after the next

---
# Evaluating conditions
* `test condition`: Evaluate a condition and if the value is true returns 0 as exit status	
	* Returns nonzero as exist status if the condition is not true
* `[ condition ]`: similar as before
* `[[ condition ]]`: similar but does not perform word splitting and path name extensions. It also allows additional operators such as `&&`, `||`, `<`, `>`
* Some example of conditions (but there are much more)
	* `-a file`: file exist (deprecated in favor of `-e file`)
	* `-d file`: file exist and is a directory
	* `-f file`: file exist and is a regular file
	* `-h file`: file exist and is a symbolic link
	* `-p file`: file exist and is a named pipe (FIFO)
	* `f1 -nt f2`: file `f1` is newer than `f2`
	* `string`: string is not null
	* `-n s1`: string `s1` has nonzero length
	* `s1 == s2`: strings `s1` and `s2` are identical. With `[[ ]]`, `s2` can be a wildcard pattern
	* `s1 = s2`: same as `==` but only for `test` and `[ ]`
	 
---
# The if command
```bash
if condition1
then commands
[ elif condition 2
  then commands2 ]
.
.
.
[else commands3]
fi
```
Examples:
```bash
if [ $counter -lt 10 ]
then number=0$counter
else number=$counter
fi
```

```bash
if [ ! -d $dir ]
then
mkdir -m 7775 $dir
fi
```

---
# The for command
```bash
for x [in [list]]
do
	commands
done
```

```bash
for ((init; cond; incr))
do
	commands
done
```

Examples:
```bash
for item in `cat program_list`
do
	echo "Checking chapters for"
	echo "references to program $item...$
	grep -c "$item.[co]" chap*
done
```
```bash
for ((x=1;$x<=20;x=x+2))
do
	cat $1 chap$x
done
```

---
# The while and case commands
```bash
while condition
do
	commands
done
```

```bash
case value in
pattern1) cmds1;;
pattern2) cmds;;
esac
```

Example:
```bash
case $1 in
no|yes) response=1;;
-[tT]) rable=TURE;;
*) echo "unknown option"; exit1;;
esac
```


