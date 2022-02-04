# Working with commands

## type
- It is used to display a command's type.
- Usage: `type command`
- Examples:
    - `type ls`
    - `type cd`
    - `type cp`

## which
- It is used to display an executables location.
- Usage: `which nameOfExecutable`
- Examples:
    - `which wireshark`
    - `which stegseek`
    - `which tcpdump`

## help
- It is used to get help for shell builtins.
- Usage: `help command`
- Examples:
    - `help cd`
    - `help type`

## -h or --help
- It is a flag which is supported by many shell builtins and executables to display help for that command or executable.
- Usage: `command --help`
- Examples:
    - `mkdir --help`
    - `wireshark --help`

## man
- It is used to dispay the <i>manual</i> or <i>man page</i> of a command.
- Usage: `man command`
- Examples:
    - `man ls`
    - `man rm`
    - `man bash`

## apropos
- It is used to display appropriate commands using a search term.
- Usage: `apropos searchTerm`
- Examples:
    - `apropos network`
    - `apropos forensics`

## whatis
- It is used to display the name and one-line description of a man page matching a specified keyword.
- Usage: `whatis keyword`
- Example:
    - `whatis ls`

## alias
- It is used to give a special name to a command or a bunch of commands combined.
- Usage: `alias name='command1; command2; command3...'`
- To list all aliases just write `alias`.
- Example:
    - `alias foo='cd ~/Desktop/; mkdir test'`
    - `alias`

## unalias
- It is used to remove an alias.
- Usage: `unalias aliasName`
- Example:
    - `unalias foo`