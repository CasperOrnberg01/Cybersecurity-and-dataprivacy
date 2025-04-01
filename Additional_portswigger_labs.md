#Portswigger labs

## Mandatory labs conclusions submitted in itsLearning:

-Sql injection vulnerability in WHERE clause allowing retrieval of hidden data

-SQL injection vulnerability allowing login bypass

-Username enumeration via different responses

-Password reset broken logic

-Unprotected admin functionality

-User role can be modified in user profile


## Optional portswigger labs:
Topic: SQL injection
-SQL injection attack, querying the db type and version on oracle:
Used burp suite's proxy and intercept on to move the request to repeater, where tried injections first to determine number of columns, where responses were for me:
category=Food'+ order+by+1--  response 200 ok = 1 column
category=Food'+ order+by+2-- response 200 ok = atleast 2 columns
3 = internal server error
3 - 1 = 2 columns
then found out the oracle version with following injection: '+UNION+SELECT+BANNER,+NULL+FROM+v$version--.
Lab was done with UNION attack to receive results from the injected query.
