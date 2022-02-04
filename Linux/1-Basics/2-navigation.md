# Basic navigation commands

## pwd - present working directory
- Using this command you can print the location of the directory you are working in.
- Usage: `pwd`

## cd - change directory
- Using this command you can change your current working directory.
- Usage: `cd path_to_directory`
- It accepts both absolute and relative paths
- Shortcut for home is ~
- Shortcut for previous working directory is -
- Shortcut for someone else's home directory is ~username
- To go to home dir just type cd
- Examples: 
    - `cd ../parent`
    - `cd ./child/grandChild`
    - `cd /home/itachi/sharingan/` or `cd ~/sharingan`
    - `cd` (will take you to home dir)
    - `cd ~levi` (cd to levi's home directory)

## ls - list
- Using this command you can list the contents of any directory, as long as you have proper permissions.
- Usage: `ls path`
- The file names starting with period (.) are hidden in linux.
- To list the hidden files use -a flag.
- To print additional info about the files and directories in linux use the -l flag, it stands for long list.
- Tip: ll is an alias for ls -l
- It accepts relative and absolute paths.
- You can even specify multiple locations seperated by spaces.
- Use -h flag to display file sizes in human readable format rather than in bytes.
- Long list:
    - Examples:
        - `-rw-r--r-- 1 sup3r541y4n sup3r541y4n 2180 Dec  5 20:43  navigation.md`
        - `drwxr-xr-x 1 sup3r541y4n sup3r541y4n 184 Dec  5 20:41 Linux`
    - The first character represents the type of file (directory(d), file(-), symbolic link(l), character special file(c) and block special file(b))
    - The next 3 characters represent the file permissions of the owner (read(r), write(w) and execute(x))
    - Read:
        - File: Allows a file to be opened and read.
        - Directory: Allows a directory’s contents to be listed if the execute attribute is also set.
    - Write:
        - File: Allows a file to be written to or truncated; however, this attribute does not allow files to be renamed or deleted. The ability to delete or rename files is determined by directory attributes.
        - Directory: Allows files within a directory to be created, deleted, and renamed if the execute attribute is also set.
    - Execute:
        - File: Allows a file to be treated as a program and executed. Program files written in scripting languages must also be set as readable to be executed.
        - Directory: Allows a directory to be entered, e.g., cd directory .
    - The next 3 characters represent the file permissions of the group.
    - The next 3 characters represent the file permissions of everyone else.
    - Next is the number of hard links of the file.
    - Next is the username of the owner.
    - And then comes the group which owns the file.
    - The numbers after than repesent the size of the file in bytes
    - Then comes the date and time of file's last modification
    - And at last comes the name of the file
- Examples:
    - `ls` (List current directory)
    - `ls -al` (List everything including hidden files and mke it a long list)
    - `ls pathToFileOrDirectory`
    - `ll` (alias for ls -l)