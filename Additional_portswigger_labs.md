#Portswigger labs

## Mandatory labs conclusions submitted in itsLearning:

-Sql injection vulnerability in WHERE clause allowing retrieval of hidden data

-SQL injection vulnerability allowing login bypass

-Username enumeration via different responses

-Password reset broken logic

-Unprotected admin functionality

-User role can be modified in user profile


# Optional portswigger labs:
## Topic: SQL injection

### -SQL injection attack, querying the db type and version on oracle:

Used burp suite's proxy and intercept on to move the request to repeater, where tried injections first to determine number of columns, where responses were for me:

category=Food'+ order+by+1--  response 200 ok = 1 column

category=Food'+ order+by+2-- response 200 ok = atleast 2 columns

3 = internal server error

3 - 1 = 2 columns

then found out the oracle version with following injection: '+UNION+SELECT+BANNER,+NULL+FROM+v$version--.

Lab was done with UNION attack to receive results from the injected query.
<br>
<br>
### Lab: SQL injection attack, querying the database type and version on MySQL and Microsoft
- Used burp suite's proxy to access the lab site, intercepted request and sent it to repeater. On repeater, first I had to verify the number of columns:  ' ORDER BY 3--+ resulted in internal sever error and  ' ORDER BY 2--+ resulted in ok. So 2 columns. After that I had to verify what columns contain text with ' UNION SELECT 'a','a'#. And the final step was to find out what database version (microsoft MySQL).
<br>
<br>

### Lab: SQL injection attack, listing the database contents on non-Oracle databases
- Number of columns: 2, '+ORDER+BY+2--%2b+. Columns with text: '+UNION+SELECT+'abc','def'--. List of tables: '+UNION+SELECT+table_name,+NULL+FROM+information_schema.tables--.Table w/ user credentials: users_pzlkhx.
- table names "'+UNION+SELECT+column_name,+NULL+FROM+information_schema.columns+WHERE+table_name='users_pzlkhx'--" ---> username_hhuwil / password_nlnnrt
- Admin credentials: "'+UNION+SELECT+username_hhuwil,+password_nlnnrt+FROM+users_pzlkhx--" --->  Lab solved, admin credentials displayed.
- Longer process than on previous lab, but same approach but this time also had seek for tables where login credentials are stored.
- 
<br>
<br>

## Topic: Authentication
### -Username enumeration via subtly different responses

Lab's purpose was to add payload and list of possible usernames and then use grep - extract to find the error message. then u had to watch for one error message that differs from the others to find the username, however i got annoyed by this part and thought if i could just do clusterbomb attack, but it took long so had to stick with the original method, enumerating username first. In the grep section i didn't "fetch" the error response so first it didn't go through. I finally got the username, when i noticed one of the error messages differed from others, missing a dot from "Invalid username or password." After this i swapped payload position to password section and pasted the candidate password list in. I found the password by seeing no error message linked to it, leaving the warning field blank.
