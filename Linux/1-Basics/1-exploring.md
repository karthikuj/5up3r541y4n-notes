# Exploring the filesystem

## file command
- In Linux file extensions don't mean anything, you could name `.txt` file `image.jpeg` and it would still work.
- So how do we identify what type of file it really is? This is where file command comes in.
- Usage: `file pathToFile`
- Example:
    - `file ~/Pictures/thousandYearsOfPain.jpeg`

## less
- Very frequently we feel the need to check the contents of the file. We can go ahead and open it in a GUI text editor, but that is not the linux way.
- Usage: `less pathToFile`
- Subcommands:
    - `q` (Quit)
    - `PAGE UP` or `b` (Scroll back one page)
    - `PAGE DOWN` or `space` (Scroll forward one page)
    - `Up arrow` (Scroll up one line)
    - `Down arrow` (Scroll down one line)
    - `G` (Move to the end of the text file)
    - `1G` or `g` (Move to the beginning of the text file)
    - `/characters` (Search forward to the next occurrence of characters)
    - `n` (Search for the next occurrence of the previous search)
    - `h` (Display help screen)
    - `q` (Quit)
- Less is more

## Symbolic links
- When viewed in long list (`ll`) symbolic links seem to have the filetype `l`.
- Symbolic links are just like pointer variables, but instead of pointing to a variable they point to a file.
- So the original file can now be referenced in two ways, either through the real file name or the name of the symlink.
- If you write something to the symbolic link, the referenced file is written to.
- When you delete a symbolic link, however, only the link is deleted, not the file itself. If the file is deleted before the symbolic link, the link will continue to exist but will point to nothing.
- Examples:
    - `ln -s ninja.scroll secret/forbidden.jutsu`
    - `ln -s acev2.txt ace.txt`

## Hard links
- By default, every file has a single hard link that gives the file its name.
- When we create a hard link, we create an additional directory entry for a file.
- Unlike a symbolic link, when you list a directory containing a hard link, you will see no special indication of the link.
- A hard link cannot reference a file outside its own file system. This means a link cannot reference a file that is not on the same disk partition as the link itself.
- A hard link may not reference a directory.
- If you write something to the hard link, the referenced file is written to.
- When a hard link is deleted, the link is removed, but the contents of the file itself continue to exist (that is, its space is not deallocated) until all links to the file are deleted.
- Examples:
    - `ln momo dimsums`