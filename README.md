# OverTheWire:Bandit-(Keshav Bansal)(230554)

### Bandit Level 0
In the level 0 of the game we have to log into the game using the `ssh` command.

SSH or Secure Shell is a network protocol that allows secure communication between two computers over an unsecured network. It provides a secure channel over an insecure network by using encryption to authenticate and encrypt data transmitted between the two systems. SSH is commonly used for remote login to shell accounts on Unix/Linux systems, but it can also be used for a variety of other purposes such as secure file transfer (SFTP), port forwarding, and tunneling.

`ssh -p 2220 bandit0@bandit.labs.overthewire.org`

Passsword : bandit0

-----------------------------------------------------------------------------

### Bandit Level 0 to Level 1
The password is in *readme* file in home directory.

Using `cat readme` to view the contents of the file.

Password : NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL

Now since we have obtained the password to log into the next level we can logout form this level using command `exit` or `logout` .

------------------------------------------------------------------------------

### Bandit Level 1 to Level 2
Now we login into Level 1 of the game with the command `ssh -p 2220 bandit1@bandit.labs.overthewire.org` and password from the previous level.

The password is stored in file with name as  -. Since the filename starts with a dash (-) we cannot directly read the file using the general commands because dash is generally used by commands to specify options and arguments.
To view contents of file use `cat <-` or `more -`.

Password : rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi

Now since we have obtained the password to log into the next level we can logout form this level using command `exit` or `logout` .

--------------------------------------------------------------------------------

### Bandit Level 2 to Level 3
Now we login into Level 1 of the game with the command `ssh -p 2220 bandit2@bandit.labs.overthewire.org` and password from the previous level.

The password is stored in file with spaces in its name. `more` or `cat` command by default doesnt perceive a filename with spaces because the general syntax for Linux commands is  `command [options] argument1 argument2` here, the arguments are separated by spaces so if we try to use filenames with spaces directly, it will be treated as separate arguments rather than just one argument.

To view file contents we will have to use :

    `more "spaces in this filename"` or `cat "spaces in this filename"` : Here the entire name in `""` will be read as a single file name.

    or

    `more spaces\ in\ this\ filename` or `cat spaces\ in\ this\ filename` : Here the backslashes `\` cancels the more to read spaces .

Password : aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG

Now since we have obtained the password to log into the next level we can logout form this level using command `exit` or `logout` .

------------------------------------------------------------------------------------

### Bandit Level 3 to Level 4
Now we login into Level 1 of the game with the command `ssh -p 2220 bandit3@bandit.labs.overthewire.org` and password from the previous level.

The password is stored in hidden file in inhere directory .

So first we use `cd inhere` to change directories.

Then use `ls -a` to show all (including hidden ones) files and directories.

Use `cat .hidden` or `more .hidden` to access the contents of hidden file .

`.` before the filename hides the file/ directory .

Password : 2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe

Now since we have obtained the password to log into the next level we can logout form this level using command `exit` or `logout` .

--------------------------------------------------------------------------------------

### Bandit Level 4 to Level 5
Now we login into Level 1 of the game with the command `ssh -p 2220 bandit4@bandit.labs.overthewire.org` and password from the previous level.

First we move to the inhere directory using `cd inhere`. `ls -a` lists all the files and directories in it. We see that there are 10 Dash file in the inhere directory. Since the password is stored in only human readable file i.e. the files in the directory will have Binary data type except for one which will have humanly readable which will be ASCII.

To find such file in directory we use `file ./*` . This command gives the filetype of all the files it the current directory i.e. inhere. We can see that only the `-file07` file has ASCII filetype. So we can read this file using `cat <-file07`.

Password : lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR

Now since we have obtained the password to log into the next level we can logout form this level using command `exit` or `logout` .

---------------------------------------------------------------------------------------

### Bandit Level 5 to Level 6
Now we login into Level 1 of the game with the command `ssh -p 2220 bandit5@bandit.labs.overthewire.org` and password from the previous level.

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

Now since we have obtained the password to log into the next level we can logout form this level using command `exit` or `logout` .

--------------------------------------------------------------------------------------------
### Bandit Level 6 to Level 7
Now we login into Level 1 of the game with the command `ssh -p 2220 bandit6@bandit.labs.overthewire.org` and password from the previous level.

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

Now since we have obtained the password to log into the next level we can logout form this level using command `exit` or `logout` .

--------------------------------------------------------------------------------------------------

### Bandit Level 7 to Level 8
Now we login into Level 1 of the game with the command `ssh -p 2220 bandit7@bandit.labs.overthewire.org` and password from the previous level.

The password for the next level is stored in the file data.txt next to the word millionth.

To read this line we will use grep command. `grep millionth *` will output all the line in the directory which have millionth word.

For finding the line in a specific file such as data.txt use : `grep millionth data.txt` .

Password : TESKZC0XvTetK0S9xNwm25STk5iWrBvP

Now since we have obtained the password to log into the next level we can logout form this level using command `exit` or `logout` .

---------------------------------------------------------------------------------------------------

### Bandit Level 8 to Level 9
Now we login into Level 1 of the game with the command `ssh -p 2220 bandit8@bandit.labs.overthewire.org` and password from the previous level.

The password for the next level is stored in the file data.txt and is the only line of text that occurs only once.

Use `sort` to sort the data and then use `uniq -u` to print the lines which occur only once.

Command is `sort data.txt | uniq -u`

or 

Use `sort` function to sort the data . Then on sorted output use `uniq -c` to count the number of all different kind of lines appearing.

Now this `uniq -c` outputs the data in 2 column format so using using `-sort k 1n` we will sort the data on the basis of their occurance in the file.

Finally use `head -1` and we get the line which only repeats once in the output.

Command is `sort data.txt | uniq -c | sort -k 1n | head -1`

Password : EN632PlfYiZbn3PhVK3XOGSlNInNE00t

Now since we have obtained the password to log into the next level we can logout form this level using command `exit` or `logout` .

`NOTE: uniq command only detects adjacent duplicates hence it is important to use sort function before using uniq`

--------------------------------------------------------------------------------------------------------

### Bandit Level 9 to Level 10
Now we login into Level 1 of the game with the command `ssh -p 2220 bandit9@bandit.labs.overthewire.org` and password from the previous level.

To read human-readble strings in file we can use `strings` command in linux .

The strings command in Unix-like operating systems is used to extract printable characters from a binary file. It essentially scans the file for sequences of printable characters and displays them to the user. Here's a detailed explanation of its functionality and usage:
Purpose: The primary purpose of the strings command is to extract human-readable text strings from binary files. Binary files often contain strings of characters embedded within them, such as error messages, debug information, or other textual data. The strings command helps to extract and display these strings, making it easier for users to analyze the contents of binary files.

The code will be as follows : `strings data.txt | grep ===` to filter human-readble lines that contain `("===")` within them.

Password : G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s

Now since we have obtained the password to log into the next level we can logout form this level using command `exit` or `logout` .

----------------------------------------------------------------------------------------------------------

### Bandit Level 10 to Level 11
Now we login into Level 1 of the game with the command `ssh -p 2220 bandit10@bandit.labs.overthewire.org` and password from the previous level.

The password is encoded in `base64` inside data.txt .

Base64 is a binary-to-text encoding scheme that represents binary data in an ASCII string format by converting it into a sequence of printable characters. In Base64 encoding, every three bytes of binary data are represented as four printable ASCII characters.

So we will use `base64 data.txt -d`

Password : 6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM

Now since we have obtained the password to log into the next level we can logout form this level using command `exit` or `logout` .

-------------------------------------------------------------------------------------------------------------

### Bandit Level 11 to Level 12
Now we login into Level 1 of the game with the command `ssh -p 2220 bandit11@bandit.labs.overthewire.org` and password from the previous level.

The password is in data.txt file encoded in `ROT13` format .

To decode the file we will use translate `tr` command to rotate all the letters .

The tr command in Unix-like operating systems is primarily used for translating or deleting characters. Its name stands for "translate" or "transliterate."

The translate command will be written as follows `tr [A-Za-z] [N-ZA-Mn-za-m]` .

We have to translate the data of data.txt so we will use :

`cat data.txt | tr [A-Za-z] [N-ZA-Mn-za-m]` .

It will the translate the data of the output of cat command i.e. the data of data.txt .

The output is as follows:

The password is JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv

Password : JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv

Now since we have obtained the password to log into the next level we can logout form this level using command `exit` or `logout` .

--------------------------------------------------------------------------------------------------------------------

### Bandit Level 12 to Level 13
Now we login into Level 1 of the game with the command `ssh -p 2220 bandit12@bandit.labs.overthewire.org` and password from the previous level.

The file is a `hexdump` so first use `xxd -r data.txt ans` . This will convert hexdump back to a text file on which we have to operate. Now using `xxd *filename* | head` look at the first bytes of the file . Now from https://en.wikipedia.org/wiki/List_of_file_signatures check for the decompression we need to use. Rename the file accordingly and then decompress the file .

Password : wbWdlBxEir4CaE8LaPhauuOo6pwRmrDw

Now since we have obtained the password to log into the next level we can logout form this level using command `exit` or `logout` .

-------------------------------------------------------------------------------------------------------------------

### Bandit Level 13 to Level 14
Now we login into Level 1 of the game with the command `ssh -p 2220 bandit13@bandit.labs.overthewire.org` and password from the previous level.

Use the `scp` command to copy the private key file from remote system to local system. Change the permissions of this key file to be executed from `ssh -i` command and then use `ssh -i` command to login without password.

    `scp -P 2220 bandit13@bandit.labs.overthewire.org:sshkey.private ./try`
    `cd try`
    `chmod 700 sshkey.private`
    `ssh -i /home/keshav/try/sshkey.private bandit14@bandit.labs.overthewire.org -p 2220`

After logging in we can find the password in `/etc/bandit_pass/bandit14` :

`cat /etc/bandit_pass/bandit14`

Password : fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq

Now since we have obtained the password to log into the next level we can logout form this level using command `exit` or `logout` .

------------------------------------------------------------------------------------------------------------------

### Bandit Level 14 to Level 15
Now we login into Level 1 of the game with the command `ssh -p 2220 bandit14@bandit.labs.overthewire.org` and password from the previous level.

We use netcat command (nc) to connect to network `localhost` on port `30000` .

We then submit password of previous level . After that password for level 15 will surface.

`nc localhost 30000`

Password : jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt

Now since we have obtained the password to log into the next level we can logout form this level using command `exit` or `logout` .

--------------------------------------------------------------------------------------------------------------------
