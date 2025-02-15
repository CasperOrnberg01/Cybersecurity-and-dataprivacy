# Penetration Testing Report

## 1. Introduction
- **Purpose and Scope:**  
  This report includes the findings and summary of penetration testing done to the application's user register part. (localhost:8000/register)

- **Testing Schedule and Environment/Tools:**  
  Tests were done in the recommended environment: using Kali Linux via VirtualBox, Docker.
  Tests on the other hand were implemented mostly with zaproxy: HAR and HUD penetration testing. Also briefly manual testing with burp suite, what included mostly SQL-injections and Format String error vulnerability testing.
  Total time used for phase 1 testing: 5 hours


## 2. Summary
- **Key Findings and Recommendations:**  

  -*Passwords in database were not hashed*, breach into the database leaks all passwords immediatly. This also makes it an internal threat, database administrators will see user passwords which could lead to fraudulent use of the logins, for example if user has same credentials for other sites/services.
  *Recommended actions:* Use password hashing methods, like bcrypt function
 
  -*SQL-injections*, 7 instances detected with zaproxy + SQL-injection risk proven possible manually with burp.
  *Recommended actions:* Consider using 'allow list' or 'deny list' of disallowed characters in user input. Consider using prepared statements, binding variables.

  -*Path Traversal:*, 3 instances detected by zaproxy with HIGH risk but chance of exploitation is low.
  *Recommended actions:* Use allow list for allowable file extensions and exclude directory separators such as "\". Allow only a single "." -character in file name to prevent chances to abuse it for exploitation.
 

- **General Assessment of the System’s Security Posture:**  
  System has plenty of possible risks, however the HIGHEST risk now is that there is no hashing in database for the passwords. This causes severe risk for leaking of user credentials, internal threat ---> where administrators impersonate user or try to breach into users other platform accounts with the same password.
  System also had alot of threats, such as weaknesses for different kinds of SQL injections, Format string error, and missing Anti-clickjacking errors. Rest of issues are not considered  really as a threat, more like a flaw.


## 3. Findings and Categorization

- **Categorization:**
  - **Red (Critical):**  
    -Passwords in database not hashed ---> All user info in db are in high risk if breach happens, mostly password since people tend to use same passwords across different platforms. Also this causes internal threat, since administrators see user password in plain text.
    -Path traversal ---> attacker might access files, or directories that are located outside the web document's root dir
    -SQL-injections ---> SQL injections to manipulate page results are possible, where zap got 7 hits, and after manually analyzing with burp suite, it seems that sql-injections in correct form can pose a threat to this system. Sql injections also were able to cause flaws in assinging roles for registering users.

  - **Yellow (Medium):**  
    -Content security policy - Header Not Set ---> can be used to steal data or spread malware from the site.
    -Format string errors ---> attacker might be able to manipulate/read system or its data.
    -Missing anti-clickjacking Header ---> clickjacking can manipulate users to click something that wasnt meant to do.

  - **Green (Low):**  
    -Application error disclosure ---> error that could reveal attacker sensitive info, such as location of files etc.. to carry out more and different types of attacks
    -X-Content-Type-Options Header Missing ---> allows attacker to perform content type sniffing attacks
    -User Agent Fuzzer ---> vulnerability where user agent string can be manipulated to exploit weaknesses how the system handles user agent info.
    -System lets user create account without rightful age validation...


## 4. Appendices
- **Test Reports and Supporting Evidence:**
