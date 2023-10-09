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
    - `chown` : The chown command is used to change the ownership of files and directories. Changing the user owner requires administrative access. A regular user cannot use this command to change the user owner of a file, even to give the ownership of one of their own files to another user. However, the chown command also permits changing group ownership, which can be accomplished by either root or the owner of the file.
        Ex: `sudo chown root hello.sh`

    ### Viewing File

    - `cat` : The cat command will display the entire contents of the file, hence why it is mainly recommended for smaller files where the output is limited and does not require scrolling.
    - `head` : same as cat but you can see all the above code
    - `tail` : same as head but from below
        - `-n` : specifies number of line from above

        Ex: `head -n 5 hello.txt`
    
    ### Copying File

    - `cp` : The cp command is used to copy files. Similar to the mv command, it requires at least two arguments: a source and a destination. For example, to copy the /etc/passwd file to the current directory, use the following command: 
            `cp /etc/passwd .` (. is the incdication of current directory)
    - `dd` : The dd command is a utility for copying files or entire partitions at the bit level.

            `dd if=/dev/zero of=/tmp/swapex bs=1M count=50`
        Argument | Description
        --------- | -------
        if | Input File: The input file to be read from.
        of | Output File: The output file to be written.
        bs | Block Size: The block size to be used. By default, the value is considered to be in bytes. Use the     following suffixes to specify other units: K, M, G, and T for kilobytes, megabytes, gigabytes and terabytes respectively.
        count | Count: The number of blocks to be read from the input file.   

    ### Moving File

    - `mv` : The mv command requires at least two arguments. The first argument is the source, a path to the file to be moved. The second argument is the destination, a path to where the file will be moved to. 

        Ex: `mv people.csv Work`
    
    ### Removing File

    - `rm` : The rm command is used to delete files and directories. It is important to keep in mind that deleted files and directories do not go into a "trash can" as with desktop-oriented operating systems. When a file is deleted with the rm command, it is almost always permanently gone.
        - `r` : to delete a directory, use a recursive option, either the -r or -R options. Just be careful since these options are "recursive", this will delete all files and all subdirectories
    
    ### Filtering Input

    - `grep` : The grep command is a text filter that will search input and return lines which contain a match to a given pattern.

        - REGULAR EXP
            Basic Regex Character(s) | Meaning
            ------------------------ | ---------------
            . | Any one single character
            [ ] | Any one specified character
            [^ ] | Not the one specified character
            \* | Zero or more of the previous character
            ^ | If first character in the pattern, then pattern must be at beginning of the line to match, otherwise just a literal ^
            $ | If last character in the pattern, then pattern must be at the end of the line to match, otherwise just a literal $

            Extended Regex Character(s) | Meaning
            --------------------------- | ---------
            \+ | One or more of the previous pattern
            ? | The preceding pattern is optional
            { } | Specify minimum, maximum or exact matches of the previous pattern
            | | Alternation - a logical "or"
            ( ) | Used to create groups

    ### ShutDown

    - `shutdown` : The shutdown command arranges for the system to be brought down in a safe way. All logged-in users are notified that the system is going down and within the last five minutes leading up to the shutdown, new logins are prevented.
        Ex: `sudo shutdown now` (or hh::mm from the now time)

    ### Network Config

    - `ifconfig` : The ifconfig command stands for "interface configuration" and is used to display network configuration information.
    - `ping` : The ping command is used to verify connectivity between two computers. It does this by sending packets to another machine on a network. If the sender receives a response it should be possible to connect to that machine.
        Ex: `ping -c 4 192.168.1.2` (-c: specify the no of times the ping is sent)

    ### Viewing Processes

    - `ps` : The ps command can be used to list processes.
        - `e` : Instead of viewing just the processes running in the current terminal, users may want to view every process running on the system. The -e option will display every process.
        - `f` : Provide more details.

    ### Package Management

    Package management is a system by which software can be installed, updated, queried or removed from a filesystem. In Linux, there are many different software package management systems, but the two most popular are those from Debian and Red Hat. The virtual machines for this course use Ubuntu, a derivative of Debian.

    - `apt-get update`: Updates the package list for installed packages on your system from repositories.

    - `apt-get search [keyword]` : keyword present in package

    - `sudo apt-get install [package]` : Install desired package

    - Updating all packages of the system should be done in two steps. First, update the cache of all packages available with apt-get update. Second, execute the apt-get upgrade command and all packages and dependencies will be updated.
        `sudo apt-get update`
        `sudo apt-get upgrade`
    - REMOVING
        The apt-get command is able to either remove or purge a package. The difference between the two is that purging deletes all package files, while removing deletes all but the configuration files for the package.

        An administrator can execute the apt-get remove command to remove a package or the apt-get purge command to purge a package completely from the system.
        `sudo apt-get remove [package]`
        `sudo apt-get purge [package]`

    ### Updating User Passwords

    - `passwd` : The passwd command is used to update a user’s password. Users can only change their own passwords, whereas the root user can update the password for any user.

        Field | Example | Meaning
        ------- | ------ | -------
        User Name | sysadmin | The name of the user.
        Password Status | P	| P indicates a usable password.
                              L indicates a locked password.
                              NP indicates no password.
        Change Date | 03/01/2015 | The date when the password was last changed.
        Minimum | 0 | The minimum number of days that must pass before the current password can be changed by the user.
        Maximum | 99999 | The maximum number of days remaining for the password to expire.
        Warn | 7 | The number of days prior to password expiry that the user is warned.
        Inactive | -1 | The number of days after password expiry that the user account remains active.


    
