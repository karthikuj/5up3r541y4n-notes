# Learn how to compress and archive your files

## gzip
- The gzip program is used to compress one or more files. When executed, it replaces the original file with a compressed version of the original.
- Usage: `gzip [OPTION]... [FILE]...`
- Use the `-c` flag to write on stdout, keep original files unchnged. With this we can redirect the output to a seperate file.
- Use the `-d` flag to uncompress files compressed using gzip. We can also use gunzip program for this.
- Examples:
    - `gzip file.txt`
    - `gzip -c file.txt > f.gz`
    - `gzip -d file.txt.gz`

## gunzip
- It performs the same action as the `-d` flag in gzip. It is used to uncompress files compressed by gzip.
- Usage: `gunzip [OPTION]... [FILE]...`
- Use the `-c` flag to write on stdout, keep original files unchnged. With this we can redirect the output to a seperate file.
- Examples:
    - `gunzip file.txt.gz`
    - `gunzip -c file.txt.gz > file.dat`

## bzip2
- The bzip2 program, by Julian Seward, is similar to gzip but uses a different compression algorithm that achieves higher levels of compression at the cost of compression speed.
- Usage: `bzip2 [flags and input files in any order]`
- Use the `-d` flag to uncompress files compressed using bzip2. We can also use bunzip2 program for this.
- Use `-1` for fast compression.
- Use `-9` for best compression.
- Use the `-c` flag to write on stdout, keep original files unchnged. With this we can redirect the output to a seperate file.
- bzip2 also comes with the bzip2recover program, which will try to recover damaged .bz2 files.
- Examples:
    - `bzip2 -9 file.txt`
    - `bzip2 -1 -c file.txt > f.bz2`
    - `bzip2 -d file.txt.bz2`

## bunzip2
- It performs the same action as the `-d` flag in bzip2. It is used to uncompress files compressed by bzip2.
- Usage: `gunzip [OPTION]... [FILE]...`
- Use the `-c` flag to write on stdout, keep original files unchnged. With this we can redirect the output to a seperate file.
- Examples:
    - `bunzip2 file.txt.bz2`
    - `bunzip2 -c file.txt.bz2 > file.dat`

## Archiving files
- Archiving is the process of gathering up many files and bundling them together into a single large file. 
- Archiving is often done as part of system backups.

## tar
- the tar program is the classic tool for archiving files. Its name, short for tape archive, reveals its roots as a tool for making backup tapes.
- Usage: `tar [options] pathname...`
- Use the `-c` flag to create archives.
- Use the `-f` flag to specify the archive name.
- Use the `-t` flag to list the contents of an archive.
- Use the `-x` flag to extract all the files from the archive.
- Examples:
    - `tar -cf archive.tar foo bar`
    - `tar -tvf archive.tar`
    - `tar -xf archive.tar`

## zip
- The zip program is both a compression tool and an archiver.
- Usage: `zip [options] zipfile file`
- Use the `-r` flag for recursion.
- It is possible to pipe a list of filenames to zip via the `-@` option.
- Examples:
    - `zip -r playground.zip playground`
    - `find playground -name "file-A" | zip -@ file-A.zip`

## unzip
- It is used to extract files from zip archive.
- Usage: `unzip [OPTIONS] ziparchive`
- Example:
    - `unzip test.zip`

## rsync
- This program can synchronize both local and remote directories by using the rsync remote-update protocol, which allows rsync to quickly detect the differences between two directories and perform the minimum amount of copying required to bring them into sync.
- Usage: `rsync [OPTIONS] source destination`
- Either the source or destination should be local, remote to remote is not supported.
- Examples:
    - `sudo rsync -av --delete /etc /home /usr/local /media/BigDisk/backup`
    - `rsync -av –delete rsync://archive.linux.duke.edu/fedora/linux/development/rawhide/Everything/x86_64/os/ fedora-devel`