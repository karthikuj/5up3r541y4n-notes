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
    - We can use the `size` flag to find files that are larger, smaller or equal to the specified size. A leading `+` size indicates larger, `-` indicates smaller and no sign indicates exact match. The trailing character indicates the unit of measurement. Unit symbols:
        - `b` - 512-byte blocks. This is the default if no unit is specified.
        - `c` - bytes
        - `w` - 2-byte words
        - `k` - kilobytes
        - `M` - Megabytes
        - `G` - Gigabytes

## xargs - Build and execute command lines from standard input

## touch - Manipulate file times

## stat - Display file or file system status