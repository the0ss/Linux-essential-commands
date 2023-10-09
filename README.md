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

Symbol | File Type | Description
------- | --------- | ----------
d | directory | A file used to store other files. 
\- | regular file | Includes readable files, images files, binary files, and compressed files. \
l | symbolic link | Points to another file. \
s | socket | Allows for communication between processes. \
p | pipe | Allows for communication between processes. \
b | block file | Used to communicate with hardware. \
c | character file | Used to communicate with hardware. \
