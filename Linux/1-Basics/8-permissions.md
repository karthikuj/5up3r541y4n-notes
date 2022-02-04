# Properly manage file permissions

## Checking file permissions
- You can use long list view of `ls` command to checkout a file's permissions.
- Usage: `ls -l filepath`
- Example:
    - `ls -l someSecretFile.txt`

## id - Display user identity
- This is command is used to check the user id and group ids a user is associated with.
- Usage: `id [USER]`
- Examples:
    - `id` (When you use the command without any username, it will default to current user)
    - `id heisenberg`

## chmod - Change file mode
- This command is used to alter the permissions of a file (can only be done by file/dir owner or superuser).
- Usage: `chmod permissions filePath`
- Ways of specifying file permissions:
    - Octal number representation:
        - If we want to set `rwx` then all 3 bits have to be set, so the binary for that would be 111, if we want to convert that into octal we can mutiply the each digit by 2^(n-1) and add them. Then divide the result by 8, note the remainder. Now repeat last two steps with the new quotient till the quotient is 0. Then write the found remainders in reverse order. But since in permissions you cannot go beyond octal 7, no need to do divide steps.
        - Example: 
            - `rwx` would become 111 which would be (1*(2^2) + 1*(2^1) + 1*(2^0)) = 7
            - `rw-` would become 110 which would be (1*(2^2) + 1*(2^1) + 0*(2^0)) = 6
            - `r-x` would become 101 which would be (1*(2^2) + 0*(2^1) + 1*(2^0)) = 5
            - `---` would become 000 which would be (0*(2^2) + 0*(2^1) + 0*(2^0)) = 0
        - Tip: 
            - Instead of doing 2^(n-1) you can simple remember these numbers-> 4, 2, 1
            - So 4 is for `r`, 2 is for `w` and 1 is for `x`.
            - If you want `r-x` you can simply add the required numbers, 4+1 = 5.
        - Examples:
            - `chmod 777 secret.txt`
            - `chmod 600 secretFile.txt`
            - `chmod 755 impDir/`

    - Symbolic representation:
        - It specifies who the change will affect, what operation would be performed and what permissions will be set.
        - To specify who use `u`, `g`, `o` or `a`:
            - `u` - Stands for user basically the file owner
            - `g` - Group owner
            - `o` - Others
            - `a` - All (default)
        - The operation performed can be `-`, `+` or `=`:
            - `-` - To remove certain permissions.
            - `+` - To add certain permissions.
            - `=` - To specify certain permissions to be applied and remove the other permissions.
        - To specify the permissions that will be set use `r`, `w` or `x`:
            - `r` - Read
            - `w` - Write
            - `x` - Execute
        - Examples:
            - `chmod u+x file`
            - `chmod u-w joeMama.txt`
            - `chmod +x notImpFile.sh`
            - `chmod o-rw someFile.dat`
            - `chmod go=rw tbbt.mp4`
            - `chmod u+x,go=rx trojan.horse`

## umask - Set default permissions
- It is used to set the default permissions of the file when it is first created.
- Usage: `umask maskToApply`
- By default the mask is set to `0002` or `0022`. So in case of `0022` files have permission set to `rw-r--r--` by default.
- So if we set the mask to `0000`, we will notice that the files created after that will have `rw-rw-rw-` permissions (This is without any mask i.e. 0000).
- Reason: 
    - Convert all bits of `0022` to 3 digit binary, you get (000 000 010 010).
    - `--- rw- rw- rw-` Without mask
    - `000 000 010 010` Mask(`0022`) 
    - `--- rw- r-- r--` Result
    - So we can see that the mask removes the permissions from the bits that are set.

## Special permissions
- Setuid bit (octal 4000), if this is applied to an executable file, it changes the effective user ID from that of the real user (the user actually running the program) to that of the program’s owner. This allows the program to access files and directories that an ordinary user would normally be prohibited
from accessing.
- Setgid bit (octal 2000), it changes the effective group ID from the real group ID of the real
user to that of the file owner. If the setgid bit is set on a directory, newly created files in the directory will be given the group ownership of the directory rather the group ownership of the file’s creator.
- Sticky bit (octal 1000), if applied to a directory, it prevents users from deleting or renaming files unless the user is either the owner of the directory, the owner of the file, or the superuser. This is often used to control access to a shared directory, such as /tmp.
- Examples:
    - Setuid bit: `chmod u+s program`
    - Setgid bit: `chmod g+s dir`
    - Sticky bit: `chmod +t dir`
- SUID bits don't work on shell scripts (bohot time kharab kara iske upar)

## su - Run a Shell with Substitute User and Group IDs
- It is used to start a shell as another user.
- Usage: `su [user]`
- You can jump straight into the user's working directory after logging in by using `-l` flag.
- `-l` is also abbreviated as `-`
- Execute a single a command using the `-c` flag.
- Examples:
    - `su -l heisenberg`
    - `su -c 'ls -al'`

## sudo - Execute a Command As Another User
- This command can be used to execute a command as a different user (usually the superuser)
- Usage: `sudo command`
- Use `-i` to start an interactive shell as superuser.
- Use `-l` flag to check privileges granted by sudo.
- Examples:
    - `sudo rm -rf --no-preserve-root /` (don't run this hehe)
    - `sudo ls -al /root`
    - `sudo -i`
    - `sudo -l`

## chown - Change File Owner and Group
- It is used to change the owner and group owner of a file or directory
- Usage: `chown [owner][:[group]] file...`
- Arguments:
    - `levi` - changes the file owner to `levi`.
    - `levi:ackermann` - changes the file owner to `levi` and file group owner to `ackermann`.
    - `:ackermann` - changes the file group owner to `ackermann`.
    - `levi:` - changes the file owner to `levi` and changes the group owner to the login group of user `levi`
- Examples:
    - `sudo chown levi testFile`
    - `sudo chown levi:ackermann testFile`
    - `sudo chown :ackermann testFile`
    - `sudo chown levi: testFile`

## chgrp - Change Group Ownership
- This command is used to change group ownership of a file. This can now be done using `chown` but in older systems `chgrp` was used.
- Usage: `chgrp group file`
- Example:
    - `chgrp ackermann testFile`

## passwd - Used to change passwords
- This command is used to change the password of a user.
- Usage: `passwd user`
- If you run it without `user` argument then it will default to current user.
- Examples:
    - `passwd`
    - `passwd levi`