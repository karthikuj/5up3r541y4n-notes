# Redirection

## Redirecting standard output (stdout)
- To redirect output to a file instead of stdout use `>` symbol.
- Usage: `command > fileName`
- If something is redirected to the same file again it gets overwritten.
- To append to the file instead of overwriting it, use the `>>` symbol.
- Usage: `command >> fileName`
- Trick to truncate a file: `> fileName`
- Example:
    - `ls /usr/bin > lsOutput.dat`

## Redirecting standard error (stderr)
- Redirecting standard error lacks the ease of a dedicated redirection operator. To redirect standard error, we must refer to its file descriptor.
- File descriptors 0, 1 and 2 are for stdin, stdout and stderr respectively.
- To redirect error messages to a file instead of stderr use `2>`.
- Usage: `command 2> errorFile`
- Example:
    - `ls /thisDirDoesNotExistLmao 2> lsErrors.dat`

## Redirecting Standard Output and Standard Error to One File
- There are 2 ways to do this.
- Old method: `command > fileName 2>&1`
- New method: `command &> fileName`
- To append: `command &>> fileName`
- Example:
    - `ls /thidDirDoesNotExistLmao &> output.dat`

## /dev/null
- This file is a system device often referred to as a bit bucket, which accepts input and does nothing with it.
- It can be used to supress messages.
- Example:
    - `ll /doesNotExist 2> /dev/null`

## cat - concatenate
- It is used to read one or more files and copies them to stdout.
- Usage: `cat file...`
- To concatenate multiple files and store them into another file we can use redirection.
- In the absence of filename arguments cat reads from stdin, you can use `CTRL+d` to tell cat
that it has reached end of file (EOF) on standard input.
- Examples:
    - `cat file1 file2 file3 file4`
    - `cat file[1-4] > file.cat`
    - `cat < file1`

## sort
- It is used to sort files by line and output them on stdout.
- Usage: `sort file`
- Use the `-R` or `--random-sort` flag to shuffle the lines randomly.
- Use the `-r` or `--reverse` the sorted output.
- Use the `-u` or `--unique` to output only unique lines.
- Exmples:
    - `sort characters.txt`
    - `sort -R characters.txt`
    - `sort -r characters.txt`
    - `sort -u characters.txt`
    - `sort -ru characters.txt`

## uniq - unique
- It is used to omit repeated lines from sorted data.
- Usage: `uniq file`
- To see only duplicates use `-d` or `--repeated`.
- To print only unique lines use `-u` or `--unique`.
- To ignore case differences use `-i` or `--ignore-case`.
- Examples:
    - `uniq sortedData.txt`
    - `uniq -d sortedData.txt`
    - `uniq -u sortedData.txt`
    - `uniq -i sortedData.txt`

## grep
- It is used for pattern matching i.e. it is used to search for strings and patterns in files.
- grep is a really powerful tool, and to realise the power of grep we will have to learn regex which we will cover later.
- Usage: `grep pattern file`
- To output only what matched use `-o` or `--only-matching` flag.
- To search recursively in a directory use `-r` or `--recursive` flag.
- To print the number of the line that matched use `-n` or `--line-number` flag.
- To use Perl style regex use `-P` or `--perl-regexp` flag.
- Examples:
    - `grep gohan characters`
    - `grep -o gohan characters`
    - `grep -on gohan characters`
    - `grep -rn itachi`
    - `grep -Po [0-9]+\.[0-9]+\.[0-9]+\.[0-9]+ network.txt`

## wc - word count
- It used to show the number of lines, words and bytes in a file.
- Usage: `wc file`
- Use the `-l` or `--lines` flag to output only number of lines.
- Use the `-w` or `--words` flag to output only number of words.
- Use the `-c` or `--bytes` flag to output only number of bytes.
- Examples:
    - `wc file.txt`
    - `wc -l file.txt`
    - `wc -w file.txt`
    - `wc -c file.txt`
    - `wc -lwc file.txt` is same as `wc file.txt`

## head
- It is used to print the first few lines of a file.
- Usage: `head fileName`
- By default it prints the first 10 lines of the file but it can be changed using `-n` or `-<number>`
- Examples:
    - `head fileName`
    - `head -n 20 fileName` or `head -20 fileName`

## tail
- It is used to print the last few lines of a file.
- Usage: `tail fileName`
- By default it prints the last 10 lines of the file but it can be changed using `-n` or `-<number>`
- Examples:
    - `tail fileName`
    - `tail -n 20 fileName` or `tail -20 fileName`

## tee
- It is used to read from stdin and output to stdout and files.
- Usage: `tee fileName...`
- The real power of tee comes with pipelines.
- Example:
    - `tee theseFilesNeedToHaveSameContent*.txt`

## pipelines - |
- It can be used to <i>pipe</i> the output of a command into the stdin of another.
- Usage: `command1 | command2`
- Example:
    - `ll /usr/bin | less`
    - `cat someFile | sort | uniq | tee sortedFile`
    - `cat someFile | sort | uniq | grep -Porn [0-9]+\.{3}[0-9]+ | tee ipAddresses.txt`
    - `cat someFile | sort | uniq | head -5`
    - `cat someFile | sort | uniq | grep -Porn [0-9]+\.{3}[0-9]+ | wc`

## Difference b/w redirection and pipeline
- The redirection operator connects a command with a file, while the pipeline operator connects the output of one command with the input of a second command.
