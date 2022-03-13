## Fuzzing
- Add payload positions to parameters and use pre-built wordlists of fuzz strings to test a high volume of different inputs in quick succession.
- Easily identify differences in responses by comparing HTTP status codes, response times, lengths, and so on.
- Use grep matching rules to quickly identify occurrences of keywords, such as error, invalid, SELECT, SQL, and so on.
- Apply grep extraction rules to extract and compare the content of interesting items within responses.

## Engineering informative responses
- submitting an invalid parameter value might lead to a stack trace or debug response that contains interesting details. You can sometimes cause error messages to disclose the value of your desired data in the response. 

## Common sources of information disclosure
### Files for web crawlers
- /robots.txt
- /sitemap.xml

### - Directory listings
- Web servers can be configured to automatically list the contents of directories that do not have an index page present.

### Developer comments
- comments can sometimes be forgotten, missed, or even left in deliberately because someone wasn't fully aware of the security implications. Although these comments are not visible on the rendered page, they can easily be accessed using Burp, or even your browser's built-in developer tools. 

### Error messages
- One of the most common causes of information disclosure is verbose error messages. As a general rule, you should pay close attention to all error messages you encounter during auditing. 

### Debugging data
- For debugging purposes, many websites generate custom error messages and logs that contain large amounts of information about the application's behavior. While this information is useful during development, it is also extremely useful to an attacker if it is leaked in the production environment.

### Source code disclosure via backup files
- These temporary files are usually indicated in some way, such as by appending a tilde (~) to the filename or adding a different file extension. Requesting a code file using a backup file extension (.bak) can sometimes allow you to read the contents of the file in the response.

### Information disclosure due to insecure configuration
- Websites are sometimes vulnerable as a result of improper configuration. This is especially common due to the widespread use of third-party technologies, whose vast array of configuration options are not necessarily well-understood by those implementing them. For example, the HTTP TRACE method is designed for diagnostic purposes. If enabled, the web server will respond to requests that use the TRACE method by echoing in the response the exact request that was received. This behavior is often harmless, but occasionally leads to information disclosure, such as the name of internal authentication headers that may be appended to requests by reverse proxies. 