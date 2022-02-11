# Find what you need with ease

## locate - Find files the easy way
- locate has a database of pathnames through which we can search for files.
- The locate database is created by another program called updatedb.
- Usage: `locate [OPTIONS] searchString`
- Examples:
    - `locate bin/zip` (This will try to find all files that begin with "zip" in the bin/ directory)
    - `locate zip | grep bin` 

## find - Find files the hard way
- find command can be used for finding files in directory.
- The real power of find comes when we use it to find very specific files using different options, tests and actions.
- Usage: `find directory [OPTIONS]`
- Tests
    - We can use `-type` flag to specify the type of file we want to find. Types of files:
        - `d` - directories
        - `f` - regular files
        - `b` - block special device file
        - `c` - character special device file
        - `l` - symbolic link
    - We can use the `-name` flag to find files that match that name or pattern
    - We can use the `-size` flag to find files that are larger, smaller or equal to the specified size. A leading `+` size indicates larger, `-` indicates smaller and no sign indicates exact match. The trailing character indicates the unit of measurement. Unit symbols:
        - `b` - 512-byte blocks. This is the default if no unit is specified.
        - `c` - bytes
        - `w` - 2-byte words
        - `k` - kilobytes
        - `M` - Megabytes
        - `G` - Gigabytes
    - We can use `-cmin` flag to match files or directories whose content or attributes were last modi-
fied exactly n minutes ago, also every test with numerical value can be used with the `+`/`-` symbols as well.
    - Use the `-cnewer` to find files/directories which are newer than the file passed as value to this flag.
    - `-iname` is like `name` but case-insensitive.
    - We can use the `-mmin` flag to Match files or directories whose contents were last modified n minutes ago.
    - `-nouser` and `-nogroup` can be used to find files and directories that don't belong to a valid user and valid group respectively.
    - Use `-perm` flag to find files which have permission set to the given value.
    - With `-user` flag we can match files or directories belonging to user name . The user may be expressed by a username or by a numeric user ID.
- Operators - These are used to form logical operations to match files
    - `-and` - match if both tests are true. (shorthand version - `-a`)
    - `-or` - match if atleast one test is true. (shorthand version - `-o`)
    - `-not` - negate the test i.e. match if the test following the operator is false. (shorthand version `!`)
    - `()` - group test and operators together to form larger expressions. Since they are special characters they need to be escaped when used as arguments for a command.
- Predefined Actions - We can use these to perform a specifc set of actions on the list of result we get from the find command.
    - `-delete` - Delete the currently matching file.
    - `-ls` - Perform the equivalent of `ls -dils` on the matching file.
    - `-print` - Output the full pathname of the matching file to standard output. This is the default action if no other action is specified.
    - `-quit` - Quit once match hash been made.
- User-Defined Actions - Other than the actions listed in predefined actions, we can also invoke arbitrary commands.
    - `-exec` - It is used like this: `-exec <command> {} ;`, example: `-exec rm '{}' ';'`. Here `{}` is like a placeholder for the filepath `find` command found and since braces and semi-colons are special characters they need to be quoted or escaped.
    - `-ok` - Using this we can execute a user defined action interactively, in this the user is prompted before the action takes place. Usage is same as `-exec`.
    - When we use `-exec` the command is executed for each of the files found. But sometimes we need to execute the command once with all the files found. In those cases we can replace the `;` in `-exec` with a `+` sign. Example: `find ~ -type f -name 'foo*' -exec ls -l '{}' +`
- Unix-like systems allow embedded spaces (and even newlines!) in filenames. This causes problems for programs like `xargs` that construct argument lists for other programs. An embedded space will be treated as a delimiter. To solve this we cn use `-print0` in find command, which produces null-separated output
- Options - used to control the scope of a find search.
    - `-depth` - Direct find to process a directory’s files before the directory itself. This option is automatically applied when the -delete action is specified.
    - `-maxdepth levels` - Set the maximum number of levels that find will descend into a directory tree when performing tests and actions.
    - `-mindepth levels` - Set the minimum number of levels that find will descend into a directory tree before applying tests and actions.
    - `-mount` - Direct find not to traverse directories that are mounted on other file systems.
    - `-noleaf` - Direct find not to optimize its search based on the assumption that it is searching a
Unix-like file system. This is needed when scanning DOS/Windows file systems and CD-ROMs.
- Examples:
    - `find ~`
    - `find ~ | wc -l`
    - `find ~ -type d`
    - `find ~ -type f -user sup3r541y4n`
    - `find ~ -type f -name "*.JPG" -size +1M`
    - `find ~ \( -type f -not -perm 0600 \) -or \( -type d -not -perm 0700 \)`
    - `find ~ -type f -name '*.bak' -delete`
    - `find ~ -type f -name 'foo*' -exec ls -l '{}' ';'`

## xargs - Build and execute command lines from standard input
- This command takes input from stdin and turns it into an argument list for a specified command.
- the xargs command has the `--null` (or `-0` ) option, which accepts null-separated input. Useful when we use `-print0` in find command.
- Example:
    - `find ~ -type f -name 'foo*' -print | xargs ls -l`

## touch - Manipulate file times
- Touch is used to manipulate timestamps of a file, like access time and modification time.
- If no option is specified it will just make an empty file.
- Usage: `touch [OPTIONS] [FILE]`
- Examples:
    - `touch file.dat`
    - `touch -t 01301030 file.dat`
    - `touch -d "Nov 5" file.dat`

## stat - Display file or file system status
- The stat command reveals all that the system understands about a file and its attributes.
- Usage: `stat file`
- Example:
    - `stat file.dat`