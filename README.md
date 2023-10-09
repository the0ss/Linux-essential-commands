# Linux Essential Commands

***Most Command follow a simple pattern of syntax*** : command [options] [arguments] \
**Options :** Options can be used to alter the behavior of a command. \
**Arguments:** Arguments are required by commands, they are the things that we are working on.

- ls : Listing of information about files(by default asc).
    - l : long display
    - r : reverse(desc)
    - s : sort by size
    - t : sort by timestamp
- pwd : Present working directory
- cd : changing directories
    - .. : always represents one directory higher relative to the current directory, sometimes referred to as the parent directory.
    - . : character always represents your current directory.
    - ~ : The home directory of the current user is represented by the ~ character. As stated above, you always begin as the sysadmin user, whose home is located at /home/sysadmin. To return to your home directory at any time

`-rw-r--r-- 1 root   root  18047 Dec 20  2017 alternatives.log`       
`drwxr-x--- 2 root   adm    4096 Dec 20  2017 apache2`
FileType Permission HardLinkCount UserOwner GrpOwner FileSize TimeStamp FileName 

Symbol | File Type | Description
------- | --------- | ----------
d | directory | A file used to store other files. 
\- | regular file | Includes readable files, images files, binary files, and compressed files. 
l | symbolic link | Points to another file. 
s | socket | Allows for communication between processes. 
p | pipe | Allows for communication between processes. 
b | block file | Used to communicate with hardware. 
c | character file | Used to communicate with hardware. 

- `su`: The su command allows you to temporarily act as a different user. It does this by creating a new shell.
- `sudo` : The sudo command allows a user to execute a command as another user without creating a new shell. Instead, to execute a command with administrative privileges, use it as an argument to the sudo command. Like the su command, the sudo command assumes by default the root user account should be used to execute commands.
    - `u` : The sudo command can be used to switch to other user accounts as well. To specify a different user account use the -u option.

- `chmod` : The chmod command is used to change the permissions of a file or directory. Only the root user or the user who owns the file is able to change the permissions of a file.
    - `chmod [<SET><ACTION><PERMISSIONS>]... FILE`
    - SET
        Symbol | Meaning
        ------- | -------
        u | User: The user who owns the file.
        g | Group: The group who owns the file.
        o | Others: Anyone other than the user owner or member of the group owner.
        a | All: Refers to the user, group and others.
    - ACTION
        Symbol | Meaning
        ------- | -------
        \+ | Add the permission, if necessary
        = | Specify the exact permission
        \- | Remove the permission, if necessary
    - PERMISSION
        Symbol | Meaning
        ------- | -------
        r | read
        w | write
        x | execute
    
