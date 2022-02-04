# Configure and manage the environment

## printenv
- This command is used to print environment variables.
- Usage: `printenv [OPTION]... [VARIABLE]...`
- If used without any argument it prints all the environment variables.
- Examples:
    - `printenv`
    - `printenv HOME`
    - `printenv USER`
    - `printenv PWD SHELL`
- You can also print the value of environment variables using `echo`.
- Example:
    - `echo $HOME`

## set - Set shell options 
- The set command, when used without options or arguments, will display both the shell and environment variables, as well as any defined shell functions.
- Example:
    - `set`

## Modifying environment variables:
- You can modify variables by assigning them a new value using the assignment operator.
- Example:
    - `PATH=$PATH:$HOME/bin`
    - `foo="Value"`

## export
- The export command tells the shell to make the contents of PATH available to child processes of this shell.
- Usage: `export variable`
- Example:
    - `export foo`
    - `export` (all exported variables)

## Login shells
- A Login shell is created after a successful login of user. For example, when you login t a Linux system via terminal, SSH or switch to user with `su -` command.

## Non-login shells
- Non Login Shell is the shell, which is started by the login shell. For example, A shell which you started from another shell or started by a program etc.

## Startup Files for Login Shell Sessions
- `/etc/profile` - A global configuration script that applies to all users.
- `~/.bash_profile` - A user’s personal startup file. It can be used to extend or override settings in the global configuration script.
- `~/.bash_login` - If ~/.bash_profile is not found, bash attempts to read this script.
- `/.profile` - If neither ~/.bash_profile nor ~/.bash_login is found, bash attempts to read this file. This is the default in Debian-based distributions, such as Ubuntu.

## Startup Files for Non-Login Shell Sessions
- `/etc/bash.bashrc` - A global configuration script that applies to all users.
- `~/.bashrc` - A user’s personal startup file. It can be used to extend or override settings in the global configuration script.

## Check if you run a login shell or non-login shell
- `echo $0`
- If the above command outputs a string starting with hyphen(-), then it is a login shell else it is a non-login shell
- Examples:
    - `-bash` (login shell output)
    - `bash` (non-login shell output)

## Which Files Should We Modify?
- As a general rule, to add directories to your PATH or define additional environment variables, place those changes in `.profile`
- For everything else, place the changes in `.bashrc`.

## source
- The changes we have made to our `.bashrc` will not take effect until we close our terminal session and start a new one because the `.bashrc` file is read only at the beginning of a session. However, we can force bash to reread the modified `.bashrc` file with the following command.
- Example:
    - `source ~/.bashrc`