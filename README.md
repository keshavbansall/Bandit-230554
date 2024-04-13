# Bandit-(Keshav Bansal)(230554)
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
