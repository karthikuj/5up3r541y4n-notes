# Expansions and escaping

## Pathname expansion
- The mechanism by which wildcards work is called pathname expansion.
- Examples:
    - `echo *`
    - `echo *.md`
    - `echo [[:upper:]]*`
    - `echo test/*/sample.txt`

## Tilde expansion
- Tilde (~) expands into the path of the users home directory.
- You can also expand a specific users home directory using `~username`
- Examples:
    - `echo ~`
    - `echo ~heisenberg`

## Arithmetic expansion
- This can be used to perform arithmetic operations through expansions.
- Usage: `&((expression))`
- Examples:
    - `echo $((2 + 2))`
    - `echo $(((3 ** 3 + 3) / 10))`
    - `echo The remainder when 10 is divided by 3 is $((10 % 3))`

## Brace expansion
- This is used to text strings using a sequence or pattern.
- Usage: `{range or pattern}`
- Examples:
    - `echo Front-{A,B,C}-Back`
    - `echo {1..5}`
    - `echo {01..09}`
    - `echo {A..Z}`
    - `echo {Z..A}`
    - `echo a{A{1,2},B{3,4}}b`
    - `mkdir logFile-{01..12}-{2010..2020}`
    - `touch logFile-{01..12}-{2010..2020}/log.txt`

## Parameter expansion
- It is used to expand system variables.
- Example:
    - `echo $USER`

## Command substitution
- This allows us to use the output of a command as an expansion.
- Usage: `$(command)`
- Examples:
    - `ls -l $(which cp)`
    - `file $(ls -d /usr/bin/* | grep zip)`
- Command substitution has another syntax, it uses backquotes instead of dollar sign and parantheses.
- Usage: `` `command` ``
- Examples:
    - ``ls -l `which cp` ``

## Double quotes
- Allows you to use a string as it is, without any special characters.
- Remember, parameter expansion, arithmetic expansion, and command substitution still take place within double quotes.
- Examples:
    - `ls -l "two words.txt"`
    - `echo "$USER $((2+2)) $(cal)"`
    - `echo $(cal)` will give shitty output. Use `echo "$(cal)"` instead.

## Single quotes
- If we need to suppress all expansions, we use single quotes.
- Example:
    - `echo 'text ~/*.txt {a,b} $(echo foo) $((2+2)) $USER'`

## Escaping characters
- `\` is used to escape any character that can have a special meaning.
- Examples:
    - `echo "The balance for user $USER is: \$5.00"`
    - `mv bad\ filename.txt goodFilename.txt`

## Backslash escape sequences
- In addition to its role as the escape character, the backslash is used as part of a notation to represent certain special characters called control codes.
- Escape sequences:
    - `\a` - Bell
    - `\b` - Backspace
    - `\n` - Newline
    - `\r` - Carriage return
    - `\t` - Tab
- Examples:
    - `sleep 10; echo -e "Time's up\a`
    - `sleep 10; echo "Time's up" $'\a'`