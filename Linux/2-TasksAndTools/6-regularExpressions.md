# Match patterns like a pro

Regex or regular expressions are a way to match patterns in text, it is kind of like a language. The reason it is an important part of linux is that many programs in linux use regular experessions and by learning them you can become an advanced user.

## Metacharacters
- These are some special characters used in regular expressions to match complex patterns.
- Some of these metacharacters are: `^`, `$`, `.`, `[ ]`, `{ }`, `-`, `?`, `+`, `*`, `( )`, `|`, `\` etc.
- Moving on we'll learn about these metacharacters one by one.

## The caret (`^`) sign
- It is used to match the start of a line.
- For example if we want to match the line that starts with "Because", we can do this:
    - `^Because`

## The dollar (`$`) sign
- It is used to match the end of the line.
- For example if we want to match the line that ends with "bye", we can do this:
    - `bye$`

## Match anything using (`.`)
- So the `.` character in regular expression can match any other character.
- For example if you are matching 3 letter words starting with "ma", like "man", "map", "mam", "may", "mac" etc. We can do this:
    - `ma.`
- To be honest a better way to search for 3 letter words starting with "ma", would be this:
    - `\bma.\b`
- `\b` matches the beginning or end of a word.

## Create character classes (`[ ]`) and specify ranges (`-`)
- Character classes are a way to match a character from the given list of characters.
- For example:
    - `[bch]atman` can match "batman", "catman" or "hatman"
- The above regular expression does not match "bcfatman" as beginners sometimes misunderstand.
- You can also give ranges for the character classes using hyphen.
- Pre-built character classes:
    - `\d` - Matches any digit `[0-9]`.
    - `\D` - Matches everything except digit `[^0-9]`.
    - `\w` - Matches any character, digit or underscore `[a-zA-Z0-9_]`.
    - `\W` - Matches everything except character, digit or underscore `[^a-zA-Z0-9_]`.
    - `\s` - Matches space, tab, carriage return, line feed or form feed. `[ \t\r\n\f]`.
    - `\S` - Matches everything except space, tab, carriage return or form feed `[^ \t\r\n\f]`.
- Examples:
    - `[a-zA-Z0-9]`
    - `[a-z0-9]`
    - `[A-H]atman`
    - `[a-z\-]` - Matches lowercase characters and hyphen (`-`)

## Match a number of characters at a time (`{ }`)
- You can match some pattern a minimum, maximum or fixed number of times using braces.
- Let's create a regex for an IP address.
- An IP address is of the format: 
    - someNumberBetween0-255.someNumberBetween0-255.someNumberBetween0-255.someNumberBetween0-255
- So we can say in regex it is:
    - [0-9] (minimum 1 to maximum 3), yes it will include numbers out the range 0-255 but let's get to that later.
    - So we can write the above expression as `\d{1,3}`
    - After the number we have a full stop but we need to escape it since fullstop is a metacharacter in regex.
        - So it becomes `\d{1,3}\.`
    - Now we can to repeat this whole pattern 3 times, so it becomes:
        - `(\d{1,3}\.){3}` Here we grouped the whole previous pattern using `()`, we'll learn about it later.
    - Now at last their is one more number which can be minimum 1 digit to maximum 3 digits.
        - `(\d{1,3}\.){3}\d{1,3}`
- Now if we want to be strict with the 0-255 range we can do something like this:
    - `((1?\d{1,2}|2[0-5]{2})\.){3}(1?\d{1,2}|2[0-5]{2})`

## Match zero or one times (`?`)
- You can match a character zero or one time using `?`, it is helpful when a character may or may not exist in string.
- For example if we want to match a phone number it may or may not have `+` symbol in the beginning:
    - `\+?91-\d{10}`

## Match one or more times (`+`)
- You can match a character one or more times using `+`, it is helpful when you want the character to be matched atleast once.
- So if we want to match "Baby shark do do do do...", we can do this:
- `Baby shark (do\s?)+`

## Match zero or more times (`*`)
- You can match a character zero or more times using `*`.
- Example if we want to match any tag in html, we can do this:
    - `<.*>`

## Grouping (`( )`)
- We can group parts of our regex to specify the number of times they should be matched or to output the groups seperately (possible in many programming languages).
- Like in the IP address example we looked before we grouped parts of it to match them a specific number of times using braces `{ }`
- Examples:
    - `((1?\d{1,2}|2[0-5]{2})\.){3}(1?\d{1,2}|2[0-5]{2})`
    - `Baby shark (do\s?)+`

## Or operator (`|`)
- This is used when one of the specified pattern/string may be present but we're not sure which one.
- Example:
    - `bat(man|woman)` - This will match "batman" or "batwoman"
- The above example can also be done like this:
    - `bat(wo)?man`

## Escape character (`\`)
- Many times we want to use characters like `+`, `*`, `?`, `$` or `^` as normal characters in our regex.
- To do that we can use `\` to escape those metacharacters.
- Example:
    - `\+1 \(\d{3}\) \d{3}\-\d{4}` - Matches US phone numbers

## Negation (`^`)
- When the caret symbol is used with character classes, it negates that character class.
- Example:
    - `[^A-Z]` - Matches everything except uppercase alphabets.

## grep - global regular expression print
- This is a program that can use regular expression to find patterns in files.
- Usage: `grep [OPTIONS] <pattern> [FILE...]`
- Use the `-i` or `--ignore-case` flag to do a case-insensitive match.
- Use the `-v` or `--invert-match` flag to print lines without the pattern.
- Use the `-l` flag to only output file name of match.
- Use the `-c` flag for count of matches.
- Use the `-n` flag for number of line match was found on.
- Use the `-P` flag for perl style regex use.
- Use the `-r` flag for recursive search inside a directory.
- Use the `-o` flag to output only what matched.
- Examples:
    - `grep -Pn "Baby shark (do\s?)+" babyShark.lrc`
    - `grep -ron "John Doe" ./dir/`
    - `grep -Pic "Bat(wo)?man" batmanChronicles.script`

## find command
- You can use the `-regex` flag in `find` command to do pattern matching.
- Example:
    - `find . -regex '.*[^-_./0-9a-zA-Z].*'`

## locate command
- You can use the `--regex` flag in `locate` command to do pattern matching.
- Example:
    - `locate --regex 'bin/(bz|gz|zip)'`