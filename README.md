# oracle-regex
oracle-regex

Sample rule for regex:
1. First letter must be only uppercase or lowercase letter
2. Text length must be at least 8 characters
3. Text must contain at least one digit, uppercase and lowercase letters
4. Text must not contain a space and special characters

Using ```REGEXP_LIKE```, split it into two regex:

```
SELECT * FROM table_name 
WHERE 
   REGEXP_LIKE(column_name, '^.*[0-9]', 'c')
   AND REGEXP_LIKE(column_name, '^[a-zA-Z][a-zA-Z0-9]{7,}$', 'c');
```

Note:
- ```^.*[0-9]``` ensures there is at least one digit
- The ```^``` anchor asserts that we are at the beginning of the string
- ```[a-zA-Z]``` matches the initial letter
- ```[a-zA-Z0-9]{7,}``` matches 7 or more chars (ensuring 8 or more total) that are either ASCII letters or digits
- The ```$``` anchor asserts that we are at the end of the string
