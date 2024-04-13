# Bandit-(Keshav Bansal)(230554)
### Bandit Level 0
In the level 0 of the game we have to log into the game using the `ssh` command.

SSH or Secure Shell is a network protocol that allows secure communication between two computers over an unsecured network. It provides a secure channel over an insecure network by using encryption to authenticate and encrypt data transmitted between the two systems. SSH is commonly used for remote login to shell accounts on Unix/Linux systems, but it can also be used for a variety of other purposes such as secure file transfer (SFTP), port forwarding, and tunneling.

`ssh -p 2220 bandit0@bandit.labs.overthewire.org`

Passsword : bandit0

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

### Bandit Level 1
The password is in *readme* file in home directory.

Using `cat readme` to view the contents of the file.

Password : NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL

------------------------------------------------------------------------------

### Bandit Level 2
The password is stored in file with name as  -. Since the filename starts with a dash (-) we cannot directly read the file using the general commands because dash is generally used by commands to specify options and arguments.
To view contents of file use `cat <-` or `more -`.

Password : rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi
