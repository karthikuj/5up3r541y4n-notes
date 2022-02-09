# Write less get more

## Cursor movement
- `CTRL+A` - Move cursor to the beginning of a line.
- `CTRL+E` - Move cursor to the end of the line.
- `CTRL+F` - Move cursor one character forward; same as right arrow key.
- `CTRL+B` - Move cursor one character backward; same as left arrow key.
- `ALT+F` - Move cursor forward one word.
- `ALT+B` - Move cursor backward one word.
- `CTRL+L` - Clear the screen; similar to `clear`

## Modifying text
- `CTRL+D` - Delete the character at cursor location.
- `CTRL+T` - Transpose the character at the cursor location with the one preceding it.
- `ALT+T` - Transpose the word at cursor location with the one preceding it.
- `ALT+L` - Convert the characters from the cursor location to the end of the word to lowercase.
- `ALT+U` - Convert the characters from the cursor location to the end of the word to uppercase.

## Cutting and pasting (Killing and yanking)
- `CTRL+K` - Kill text from the cursor location to the end of line.
- `CTRL+U` - Kill text from the cursor location to the beginning of the line.
- `ALT+D` - Kill text from the cursor location to the end of the current word.
- `ALT+BACKSPACE` - Kill text from the cursor location to the beginning of the current word. If the cursor is at the beginning of a word, kill the previous word.
- `CTRL+Y` - Yank text from the kill-ring and insert it at the cursor location.

## Completion
- `TAB` - You can use `TAB` to autocomplete your commands. 
- `ALT+?` or `TAB`x2 - Display a list of possible completions. On most systems, you can also do this by pressing the tab key a second time, which is much easier.
- `ALT+*` - Insert all possible completions. This is useful when you want to use more than one possible match.

## History
- `history` - This command is used to check the command line history.
- `!<historyLineNumber>` - Repeat the command on that line in history. Example: `!72`
- `CTRL+R` - This will change command line prompt to reverse incremental search, you can search for any previous commands and press enter to enforce the found command.
- `ctrl+O` - Execute the current item in the history list and advance to the next one. This is handy if you are trying to re-execute a sequence of commands in the history list.

## History Expansion
- `!!` - Repeat the last command. It is probably easier to press the up arrow and enter. You can also write something and use `!!` to append the command with what you wrote, useful when you forget to write `sudo`. Example: `sudo !!`
- `!number` - Repeat history list item number.
- `!string` - Repeat last history list item starting with string. [DON'T USE]
- `!?string` - Repeat last history list item containing string. [DON'T USE]

## script
- This command is used to record an entire shell session.
- Usage: `script filePath`
- To end the session use `CTRL+D` or close the terminal.
- Example:
    - `script ~/Desktop/session.file`
