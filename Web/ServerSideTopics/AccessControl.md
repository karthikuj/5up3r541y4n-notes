## Vertical privilege escalation

### Unprotected functionality
- Find admin functionality
- Check robots.txt
- Brute-force locations
- The URL might be disclosed in JavaScript that constructs the user interface based on the user's role

### Parameter-based access control methods
- If there is admin=false parameter in requests or something similar try fiddling with that.
- If there is a functionality to change something related to your profile try changing your access with that. Example: {"email":"wiener@gmail.com", "roleid":2}

### Broken access control resulting from platform misconfiguration
#### Through headers
- X-Rewrite-URL: + path
- X-Original-URL: + path
- Referer: + path
- X-Custom-IP-Authorization: 127.0.0.1
- X-Originating-IP: 127.0.0.1
- X-Forwarded-For: 127.0.0.1
- X-Remote-IP: 127.0.0.1
- X-Remote-Addr: 127.0.0.1
- X-Client-IP: 127.0.0.1
- X-Host: 127.0.0.1
- X-Forwarded-Host: 127.0.0.1

- Blocked request: <br>
GET /admin/delete?username=carlos HTTP/1.1
- Circumvent: <br>
GET / HTTP/1.1<br>
X-Original-URL: /thisFileDoesNotExist <br>
The above will return 404 which indicates that the header is working <br><br>
GET /?username=carlos HTTP/1.1<br>
X-Original-URL: /admin/delete <br>
The above will circumvent the blocked request.

#### Method-based access control
- Try to change request method to POSTX
- Convert the request to use the GET method by right-clicking and selecting "Change request method".

## Horizontal privilege escalation

### User ID controlled by request parameter
- Try changing userid or any suck parameter

### User ID controlled by request parameter, with unpredictable user IDs
- The unpredictable IDs may be leaked somewhere else where users are referenced

### data leakage in redirect
- In some cases, an application does detect when the user is not permitted to access the resource, and returns a redirect to the login page. However, the response containing the redirect might still include some sensitive data belonging to the targeted user.

## Horizontal to vertical privilege escalation
-  a horizontal escalation might allow an attacker to reset or capture the password belonging to another user. If the attacker targets an administrative user and compromises their account, then they can gain administrative access and so perform vertical privilege escalation.

## Access control vulnerabilities in multi-step processes