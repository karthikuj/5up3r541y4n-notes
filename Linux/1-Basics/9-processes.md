# Manage all processes

## ps
- This command is used to view processes running on the system.
- Usage: `ps [arguments]`
- Examples:
    - `ps` (Shows list of processes associated with the current terminal session)
    - `ps aux` (This is popular set of options, used to view all running processes regardless if it is or it is not associated with the current terminal session)

## top
- It is used to view a continuously updating list of top processes sorted by CPU activity.
- Usage: `top [arguments]`
- Example:
    - `top`

## Interrupting a program
- In a terminal, pressing `CTRL+C` interrupts a program.
- Many (but not all) command line programs can be interrupted by using this technique.

## jobs
- Using this we can list the jobs that have been launched from our terminal.
- We can also check the job numbers of the programs.
- Usage: `jobs [arguments]`

## bg - Backgrounding a process
- Check the job number using the `jobs` command.
- Usage: `bg %[jobNumber]`
- Example:
    - `bg %1`

## fg - Foregrounding a process
- Check the job number using `jobs` command.
- Usage: `fg %[jobNumber]`
- Example:
    - `fg %1`

## Stopping (Pausing) a Process
- To stop a foreground process and place it in the background, press `CTRL+Z`.

## kill
- This command is used to send signals to programs, if no signal is mentioned the default signal is TERM (terminate).
- Usage: `kill -signal PID...`
- Common signals:
    - 1 (HUP) - The signal is used to indicate to programs that the controlling terminal has “hung up.”
    - 2 (INT) - Interrupt. This performs the same function as `CTRL+C` sent from the terminal. It will usually terminate a program.
    - 9 (KILL) - KILL. The signal is not sent to the process, infact the kernel immediately terminates  the program.
    - 15 (TERM) - Terminate. This is the default signal sent by the kill command. If a program is still “alive” enough to receive signals, it will terminate.
    - 18 (CONT) - Continue. This will restore a process after a STOP or TSTP signal. This signal is sent by the bg and fg commands.
    - 19 (STOP) - Stop. This signal causes a process to pause without terminating. Like the KILL signal, it is not sent to the target process, and thus it cannot be ignored.
    - 20 (TSTP) - Terminal stop. This is the signal sent by the terminal when `CTRL+Z` is pressed. Unlike the STOP signal, the TSTP signal is received by the program, but the program may choose to ignore it.
- Note that signals may be specified either by number or by name, including the name prefixed with the letters SIG.
- Examples:
    - `kill -1 13546`
    - `kill -INT 13601`
    - `kill -SIGINT 13601`

## killall
- It is used to send signals to multiple processes matching a specified program or username.
- Usage: `killall [-u user] [-signal] name...`
- Example:
    - `killall python`

## reboot
- Used to reboot your device.
- Usage: `sudo reboot`

## shutdown
- With this we can specify which of the actions to perform (halt, power down, or reboot) and provide a time delay to the shutdown event.
- Usage: `sudo shutdown [arguments]`
- Examples:
    - `sudo shutdown -h now`
    - `sudo shutdown -r now`