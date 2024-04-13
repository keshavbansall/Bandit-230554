# OverTheWire:Bandit-(Keshav Bansal)(230554)
### General Commands

---------------------------------------------------------------------------

### Bandit Level 0
In the level 0 of the game we have to log into the game using the `ssh` command.

SSH or Secure Shell is a network protocol that allows secure communication between two computers over an unsecured network. It provides a secure channel over an insecure network by using encryption to authenticate and encrypt data transmitted between the two systems. SSH is commonly used for remote login to shell accounts on Unix/Linux systems, but it can also be used for a variety of other purposes such as secure file transfer (SFTP), port forwarding, and tunneling.

`ssh -p 2220 bandit0@bandit.labs.overthewire.org`

Passsword : bandit0

-----------------------------------------------------------------------------

### Bandit Level 1
The password is in *readme* file in home directory.

Using `cat readme` to view the contents of the file.

Password : NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL

------------------------------------------------------------------------------

### Bandit Level 2
The password is stored in file with name as  -. Since the filename starts with a dash (-) we cannot directly read the file using the general commands because dash is generally used by commands to specify options and arguments.
To view contents of file use `cat <-` or `more -`.

Password : rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi

--------------------------------------------------------------------------------

### Bandit Level 3
The password is stored in file with spaces in its name. `more` or `cat` command by default doesnt perceive a filename with spaces because the general syntax for Linux commands is  `command [options] argument1 argument2` here, the arguments are separated by spaces so if we try to use filenames with spaces directly, it will be treated as separate arguments rather than just one argument.

To view file contents we will have to use :

    `more "spaces in this filename"` or `cat "spaces in this filename"` : Here the entire name in `""` will be read as a single file name.

    or

    `more spaces\ in\ this\ filename` or `cat spaces\ in\ this\ filename` : Here the backslashes `\` cancels the more to read spaces .

Password : aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG

------------------------------------------------------------------------------------

### Bandit Level 4
The password is stored in hidden file in inhere directory .

So first we use `cd inhere` to change directories.

Then use `ls -a` to show all (including hidden ones) files and directories.

Use `cat .hidden` or `more .hidden` to access the contents of hidden file .

`.` before the filename hides the file/ directory .

Password : 2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe

--------------------------------------------------------------------------------------

### Bandit Level 5
First we move to the inhere directory using `cd inhere`. `ls -a` lists all the files and directories in it. We see that there are 10 Dash file in the inhere directory. Since the password is stored in only human readable file i.e. the files in the directory will have Binary data type except for one which will have humanly readable which will be ASCII.

To find such file in directory we use `file ./*` . This command gives the filetype of all the files it the current directory i.e. inhere. We can see that only the `-file07` file has ASCII filetype. So we can read this file using `cat <-file07`.

Password : lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR

---------------------------------------------------------------------------------------

### Bandit Level 6
The password for the next level is stored in a file somewhere under the inhere directory (which itself has about 20 directories) and has all of the following properties:

`human-readable
1033 bytes in size
not executable`

To use `find` with such properties we can use :

    `-size 1033c`  : can be used to display only files of size 1033 bytes.
    
    `! -executable`  : is used to find non executable file .
    
    File is a bash command to execute it as well we use `-exec file '{}' \;` .
    
    Now to only display files of ASCII data type we use | grep ASCII 

#NOTE: `\;` is used to properly terminate the exec command .

Password : P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU

--------------------------------------------------------------------------------------------
### Bandit Level 7
The password for the next level is stored somewhere on the server and has all of the following properties:

`owned by user bandit7`

`owned by group bandit6`

`33 bytes in size`

To search the entire directory we will specify root directory as starting point using `("/")` .

In Linux, when we execute a command, there are two primary output streams: standard output (stdout) and standard error (stderr).By default, both stdout and stderr are displayed on the terminal. They are separate streams, but they are often displayed together.

To hide the error output stream we can redirect the error stream(descripitor 2) we can use :

`find / -size 33c  -user bandit7 -group bandit6 2>/dev/null`  #/dev/null: acts as a black hole for data in Linux , hence redirecting stderr to /dev/null esentially discards the data.

Then use `cat /var/lib/dpkg/info/bandit7.password` to get the password.

#Note: Using `2>/dev/null` discard all error messages. If we only want to discard error messages with a particular string we can use `2>&1` to redirect stderr to stdout then we can use `grep` command to filer out result from stdout.

eg: `find / -size 33c  -user bandit7 -group bandit6 2>&1 | grep -v "Permission denied"`

Password : z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S

--------------------------------------------------------------------------------------------------

### Bandit Level 8
The password for the next level is stored in the file data.txt next to the word millionth.

To read this line we will use grep command. `grep millionth *` will output all the line in the directory which have millionth word.

For finding the line in a specific file such as data.txt use : `grep millionth data.txt` .

Password : TESKZC0XvTetK0S9xNwm25STk5iWrBvP

---------------------------------------------------------------------------------------------------

### Bandit Level 9
The password for the next level is stored in the file data.txt and is the only line of text that occurs only once.

Use `sort` to sort the data and then use `uniq -u` to print the lines which occur only once.

Command is `sort data.txt | uniq -u`

or 

Use `sort` function to sort the data . Then on sorted output use `uniq -c` to count the number of all different kind of lines appearing.

Now this `uniq -c` outputs the data in 2 column format so using using `-sort k 1n` we will sort the data on the basis of their occurance in the file.

Finally use `head -1` and we get the line which only repeats once in the output.

Command is `sort data.txt | uniq -c | sort -k 1n | head -1`

Password : EN632PlfYiZbn3PhVK3XOGSlNInNE00t

`NOTE: uniq command only detects adjacent duplicates hence it is important to use sort function before using uniq`

--------------------------------------------------------------------------------------------------------

### Bandit Level 10
To read human-readble strings in file we can use `strings` command in linux .

The strings command in Unix-like operating systems is used to extract printable characters from a binary file. It essentially scans the file for sequences of printable characters and displays them to the user. Here's a detailed explanation of its functionality and usage:
Purpose: The primary purpose of the strings command is to extract human-readable text strings from binary files. Binary files often contain strings of characters embedded within them, such as error messages, debug information, or other textual data. The strings command helps to extract and display these strings, making it easier for users to analyze the contents of binary files.

The code will be as follows : `strings data.txt | grep ===` to filter human-readble lines that contain `("===")` within them.

Password : G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s

----------------------------------------------------------------------------------------------------------

### Bandit Level 11
