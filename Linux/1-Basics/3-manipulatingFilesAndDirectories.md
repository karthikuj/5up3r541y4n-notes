# Manipulating files and directories

## Character classes
- `[:alnum:]` (Matches any alphanumeric character)
- `[:alpha:]` (Matches any alphabetic character)
- `[:digit:]` (Matches any numeral)
- `[:lower:]` (Matches any lowercase letter)
- `[:upper:]` (Matches any uppercase letter)

## Wildcards
- `*` (Matches any character)
- `?` (Matches any single character)
- `[characters]` (Matches any character that is a member of the set <i>characters</i>)
- `[!characters]` (Matches any character that is not a member of the set <i>characters</i>)
- `[[:class:]]` (Matches any character that is a member of the specified <i>class</i>)
- Examples:
    - `*`
    - `g*`
    - `b*.txt`
    - `Data???`
    - `[abc]*`
    - `BACKUP.[0-9][0-9][0-9]`
    - `*[[:lower:]123]`

#### Note* - Wildcards can be used with any command that accepts filenames as arguments.

## cp - copy
- This command is used to copy files and directories from one place to another in the filesystem.
- Usage: `cp source... destination`
- Note that when three periods follow an argument in the description of a command (as in the preceding example), it means that the argument can be repeated.
- To copy entire directory use the recursive flag `-R`
- To copy files along with all their attributes like ownership and permissions use `-a ` or `--archive`
- Only copy the files that don't exist in the destination or have older versions of the file being copied using `-u` or `--update` 
- You can also rename them while copying them.
- Examples:
    - `cp /usr/share/wordlists/rockyou.txt ./`
    - `cp -R ~/someDir/impDir ~/secretDir/`
    - `cp /usr/bin/oldVersion /usr/bin/kisiKoPtaNhiChalega/newVersion`
    - `cp ~/Desktop/*pdf ~/Documents`
    - `cp item1 item2 dir`
    - `cp item1 item2`

## mv - move
- This command is used to move files and rename files.
- Usage: `mv file... Destination` or `mv oldName newName`
- To have the `mv` command ask for confirmation use `-i` or `--interactive` flag.
- Examples:
    - `mv oldFile newFile`
    - `mv someFile ../someDir/`
    - `mv file1 file2 file3 ../someDir/` or `mv file[1-3] ../someDir/`
    - `mv dir1 ../someDir/`
    - `mv oldDirName newDirName`

## mkdir - make directory
- This command is used to create one or more directories.
- Usage: `mkdir dir...`
- Examples:
    - `mkdir someDir`
    - `mkdir someDir ../parentDirSibling ./existingDir/existingDirChild`

## rm - remove
- This command is used to delete files and directories.
- Usage: `rm file...`
- To delete a directory recursively use `-r` or `--recursive` flag.
- To override prompts use `-f` or `--force` flag.
- Examples:
    - `rm file`
    - `rm file0 file1 file2 file3 file4 file5 file6 file7 file8 file9`
    - `rm file[[:digit:]]`
    - `rm -rf garbageDir/`