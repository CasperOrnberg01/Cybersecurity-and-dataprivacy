# Portswigger labs

## Mandatory labs conclusions submitted in itsLearning:

###  Lab: Sql injection vulnerability in WHERE clause allowing retrieval of hidden data
- I learned to commit a simple SQLi on a vulnerable application that forwards them into its database. I modified sql query to allow me to access and see the unreleased products in the “webshop”. I added quote mark after category = to close the category string and then 1=1 which makes the argument true. I also learned, that most sqli vulnerabilities are in the “where” part of select query.
<br>
<br>

### Lab: SQL injection vulnerability allowing login bypass
- I learned that application checks the used credentials by performing sql query from the credentials section. This lab also demonstrated an sqli happening in the where clause of query. Interesting part of this lab was the fact, that if the application is vulnerable enough u can bypass the log in and get it as administrator. The material had the lab pretty well covered, but I noticed that in the password field u could type anything after adding quote mark in it and it would still log in. Apparently the password was bypassed by the “—“ what was written after “administrator” in the username section, which removed the password check from where clause.
<br>
<br>

### Lab: Username enumeration via different responses
- I learned to to do username enumeration with burpsuite by looking at different responses. Finding out the username, I did brute force attack based on the gived candidate password list. I knew that username was found when lenght was different from the others, and password was right one from the status code. However, I had problems with this lab since I have norton antivirus on my pc, so everytime i started brute force attack on password, norton just blocked and moved Burp suite’s chrome.exe to quarantine and identified it as “IDP.Generic” threat. However, I had to delete every burpsuite associated file, and then disable auto-protect + auto-firewall and reinstall burpsuite and then move the files to “expections” so antivirus wont mess with them no more.
<br>
<br>

### Lab: Password reset broken logic
- I learned to exploit vulnerability, where I resetted user’s password by changing user parameter to my own username. then I received password reset token, which I just modified to “x” and set the username as “carlos”. then I was able to set carlo’s password to what ever I wanted. Then I was able to log in as “Carlos” and complete the lab.
<br>
<br>

### Lab: Unprotected admin functionality
- learned to exploit a vulnerability in unprotected admin panel, where the goal was to gain access to admin functionality: delete users. This was achieved by modifying the url to gain access to the unprotected admin panel. Some could say that it’s protection is based on the fact, that most of people wouldn’t realise to try out modifying the url to “admin-panel”,”admin”, “administrator” or etc… The admin panel was accessed by modifying the end of the url to “administrator-panel”. Now we have accessed the admin features, and we are able to delete users.
<br>
<br>

### Lab: User role can be modified in user profile
- I learned that in the lab the vulnerability was client’s ability to change the roleid to whatever client wants. This was possible, because the application had broken access control vulnerability. This lab was one example of parameter based access conjtrol methods, where application determined user’s access rights at login and stored the information, but the user is able to modify the value, which in this case was roleid. roleid by default was equal to 1 and by setting the roleid equal to 2 gained the admin rights.

# Optional portswigger labs:
## Topic: SQL injection

### Lab: SQL injection attack, querying the db type and version on oracle:

- Used burp suite's proxy and intercept on to move the request to repeater, where tried injections first to determine number of columns, where responses were for me:

- category=Food'+ order+by+1--  response 200 ok = 1 column

- category=Food'+ order+by+2-- response 200 ok = atleast 2 columns

- 3 = internal server error

- 3 - 1 = 2 columns

- then found out the oracle version with following injection: '+UNION+SELECT+BANNER,+NULL+FROM+v$version--.

- Lab was done with UNION attack to receive results from the injected query.
  
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
  
<br>
<br>

### Lab: SQL injection attack, listing the database contents on Oracle
- Same progress as before, determining the amount of columns that contain text data. Then retriueving the list of tables in the DB. After this I had to find the table containing user credentials: USERS_EGFXXT
- Column for pass: PASSWORD_EKUPDA. Column for usernames: USERNAME_QSEWBB.
- payload to retrieve logins for all users, then find admin: '+UNION+SELECT+USERNAME_QSEWBB,+PASSWORD_EKUPDA+FROM+USERS_EGFXXT--
  
<br>
<br>

### Lab: SQL injection UNION attack, determining the number of columns returned by the query
- Fastest lab I've had this far on portswigger.
- Just used Burpsuite's proxy and sent request to repeater where tried different payloads on category parameter. This lab was solved by just adding nulls to: '+UNION+SELECT+NULL--. 3 Nulls were enough for me to solve this lab.

<br>
<br>

### Lab: SQL injection UNION attack, finding a column containing text
- Done by intercepting request and sending it to repeater in Burp suite
- Pretty fast lab to complete, first determining the number of columns that are returned by query. Then when found out that is it three columns you had to replace every null one by one with a string and look for responses.
- 2nd null for me accepted a string, forwarding me to a new page where was hint what string to use.

<br>
<br>

### Lab: SQL injection UNION attack, retrieving data from other tables
- Used burp to intercept request and send it to repeater, where i determined the number of columns returned by query just like on the last labs.
- Retrieved content of users table with following payload: '+UNION+SELECT+username,+password+FROM+users--
- Logged in with the administrator credentials to complete and finish the lab

<br>
<br>

### Lab: SQL injection UNION attack, retrieving multiple values in a single column
- Dtermining number of columns: order by 3-- = internal server error, order by 2-- = status 200 ok == 2 columns
- Columns that have text: ' UNION SELECT NULL, 'a'-- == 200 ok
- Getting credentials from user table: '+UNION+SELECT+NULL,username||'~'||password+FROM+users-- == skim through credentials and find admin logins --> log in as admin
- Lab's purpose was to perform UNION injection, that returns multiple values in single column. on Previous labs the values have been on separate columns.

<br>
<br>

## Topic: Authentication
### Lab: Username enumeration via subtly different responses

- Lab's purpose was to add payload and list of possible usernames and then use grep - extract to find the error message. then u had to watch for one error message that differs from the others to find the username, however i got annoyed by this part and thought if i could just do clusterbomb attack, but it took long so had to stick with the original method, enumerating username first. In the grep section i didn't "fetch" the error response so first it didn't go through. I finally got the username, when i noticed one of the error messages differed from others, missing a dot from "Invalid username or password." After this i swapped payload position to password section and pasted the candidate password list in. I found the password by seeing no error message linked to it, leaving the warning field blank.

## Topic: Access control
### Lab: User ID controlled by request parameter
- Getting familiar with the application behaviour with given credentials, and logging in with them.
- Checked if it's client controlled, by changing given user ID to "carlos" in repeater's request, where response contained "carlos" API KEY.
- Vulnerability was that you are able to obtain same priviledge level users account access just by changing the username ID to the wanted one.

<br>
<br>

### Lab: Unprotected admin functionality with unpredictable URL
- Lab's purpose was to exploit vulnerability of the admin panel. I reviewed source code with developer tools and there was leftover JS function that revealed the admin directory. adding this to URL accessed the admin panel.
- Deleted wanted user and completed the lab.

<br>
<br>

### Lab: User role controlled by request parameter
- In burp used repeater to to observe response codes when changing cookie value "admin" from false to true.
- I completed the lab by going on the browser, using developer tools to inspect the application cookies, and there manually set admin value to true. This gave me access to admin panel, where I deleted the wanted user.

<br>
<br>

### Lab: User ID controlled by request parameter, with unpredictable user IDs
- Lab's purpose was to gain access to other user's account by finding the GUID.
- I looked for blog post that was created by user "carlos", and noticed that GET request leaked the userID for carlos.
- I sent my users get request to repeater, where I changed my GUID to the leaked carlos GUID. This gave me the API key for carlos, and completed the lab.

<br>
<br>

### Lab: User ID controlled by request parameter with data leakage in redirect
- Similar lab to the previous access control labs, where I had to obtain API key for user carlos.
- This was really easy and fast to do, since I completed the previous labs on the topic, where first I logged in with the given credentials, and saw that it takes the id of user, where I just sent it into repeater, and changed my user ID to "carlos". Then I got API key for carlos and lab completed. Redirect leaked the page for carlos.

