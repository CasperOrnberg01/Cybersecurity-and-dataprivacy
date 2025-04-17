# GDPR Compliance Checklist – Web-based Booking System

| **Result** | **Personal data mapping and minimization** |
| :----: | :--- |
| &nbsp;✅Name is not really collected, just email and age. Where age > 15 can register now in the p4 application. Email is stored as "username" in zephyr_users; table. Age as birthdate in zephyr_users; table&nbsp; | Have all personal data collected and processed in the system been<br> identified? (e.g., name, email, age, username) |
| &nbsp;✅Only email as username and age is collected. No other additional information such as address, phone number, etc... &nbsp; | Have you ensured that only necessary personal data is collected (data minimization)? |
| &nbsp;⚠️If I recall correctly, on older versios age was used to restrict to create new reservations or booking. On this phase4 version, You cannot register if you are under 15 years old.&nbsp; | Is user age recorded to verify that the booker is over 15 years old? |

---

| **Result** | **User registration and management** |
| :----: | :--- |
| &nbsp;✅⚠️Yes, registration form has TOS-agreement check box. But itself the TOS-page is empty.&nbsp; | Does the registration form (page) include GDPR-compliant consent for processing<br> personal data (e.g., acceptance of the privacy policy)?|
| &nbsp;❌⚠️Account management page exists, but Users cannot edit their data or delete their account.&nbsp; | Can users view, edit, and delete their own personal data via their account? |
| &nbsp;❌No. However with access to the database itself this is possible.&nbsp; | Is there a mechanism for the administrator to delete a reserver in<br> accordance with the "right to be forgotten"? |
| &nbsp;✅Yes.&nbsp; | Is underage registration (under 15 years) and booking functionality restricted? |

---

| **Result** | **Booking visibility** |
| :----: | :--- |
| &nbsp;✅Yes, bookings are only visible to non-logged-in users only by resource name and start-end date&nbsp; | Are bookings visible to non-logged-in users only at the resource level<br> (without any personal data)? |
| &nbsp;✅⚠️Yes, but reservers also see the "Reserver" = email.&nbsp; | Is it ensured that names, emails, or other personal data of bookers are not exposed<br> publicly or to unauthorized users? |

--- 

| **Result** | **Access control and authorization** |
| :----: | :--- |
| &nbsp;⚠️Admins can add resources and bookings, also modify them, but not delete. Reservers can add and modify them as well.&nbsp; | Have you ensured that only administrators can add, modify, and delete<br> resources and bookings? |
| &nbsp;✅⚠️Yes, system is using role-based access control, but some admin functionalities are exposed to reservers too. Also admin role should have separate panel to take modification actions.&nbsp; | Is the system using role-based access control (e.g., reserver vs. administrator)? |
| &nbsp;✅Yes, admins cannot use data for unauthorized purposes.&nbsp; | Are administrator privileges limited to ensure GDPR compliance (e.g., administrators<br> cannot use data for unauthorized purposes)? |

---

| **Result** | **Privacy by Design Principles** |
| :----: | :--- |
| &nbsp;✅Yes. &nbsp; | Has Privacy by Default been implemented (e.g., collecting the minimum data by default)? |
| &nbsp;✅Yes, user_token is hashed in zephyr_login_logs. Also only login_timestamp and ip_address visible.&nbsp; | Are logs implemented without unnecessarily storing personal data? |
| &nbsp;✅Yes.&nbsp; | Are forms and system components designed with data protection in mind<br> (e.g., secured login, minimal fields)? |

---

| **Result** | **Data security** |
| :----: | :--- |
| &nbsp;✅Yes, protections are implemented.&nbsp; | Are CSRF, XSS, and SQL injection protections implemented? |
| &nbsp;✅Yes, passwords are hashed./❌/⚠️&nbsp; | Are passwords securely hashed using a strong algorithm (e.g., bcrypt, Argon2)? |
| &nbsp;⚠️&nbsp; | Are data backup and recovery processes GDPR-compliant? |
| &nbsp;⚠️&nbsp; | Is personal data stored in data centers located within the EU? |

---

| **Result** | **Data anonymization and pseudonymization** |
| :----: | :--- |
| &nbsp;✅⚠️Personal data is mostly anonymized, logged-in users can see reserver emails though.&nbsp; | Is personal data anonymized where possible? |
| &nbsp;✅reserver_token is used instead of email.&nbsp; | Are pseudonymization techniques used to protect data while maintaining its utility? |

---

| **Result** | **Data subject rights** |
| :----: | :--- |
| &nbsp;❌No.&nbsp; | Can users download or request all personal data related to them (data access request)? |
| &nbsp;❌No.&nbsp; | Is there an interface or process for users to request the deletion of their personal data? |
| &nbsp;❌No, the account panel where consent is set to "Yes", doesnt respond.&nbsp; | Can users withdraw their consent for data processing? |

---

| **Result** | **Documentation and communication** |
| :----: | :--- |
| &nbsp;❌⚠️There is hyperlink in logical place, bottom of the page. But the privacy policy is empty.&nbsp; | Is there a privacy policy available to users during registration and easily accessible? |
| &nbsp;❌&nbsp; | Are administrators and developers provided with documented data protection practices <br>and processing activities? |
| &nbsp;❌&nbsp; | Is there a documented data breach response process (e.g., how to notify authorities <br>and users of a breach)? |

---

**Symbols used:**  
✅ Pass (a note can be added)  
❌ Fail (a note can be added)  
⚠️ Attention (a note can be added)
