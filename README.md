# cve
a page for cve
# Phpgurukul RTBS Project PHP V2.1 /aboutus.php SQL injection
# NAME OF AFFECTED PRODUCT(S)
RTBS Project PHP
# Vendor Homepage
https://phpgurukul.com/zoo-management-system-using-php-and-mysql/
# AFFECTED AND/OR FIXED VERSION(S)
## submitter
B1a2ing
## Vulnerable File
/aboutus.php
## VERSION(S)
V2.1
## Software Link
https://phpgurukul.com/?sdm_process_download=1&download_id=12723
## Root Cause
A critical SQL injection vulnerability was identified in the /aboutus.php file of the RTBS Project PH. The root cause of this issue lies in the improper handling of user input from the pagetitle parameter. This input is directly incorporated into SQL queries without sufficient sanitization or validation, allowing attackers to inject malicious SQL commands. As a result, attackers can manipulate the query, leading to unauthorized actions on the database.
## Impact
Exploiting this vulnerability can have severe consequences. Attackers may gain unauthorized access to the database, extract sensitive data, alter or delete records, and potentially gain full control of the system. In some cases, they could cause service disruptions, posing a significant risk to the overall security and continuity of the business.
## DESCRIPTION
During the security assessment of the RTBS Project PH, a critical SQL injection vulnerability was found in the /aboutus.php file. This flaw arises from insufficient validation of the pagetitle parameter, which allows attackers to inject arbitrary SQL commands. As a result, malicious users can compromise the database, potentially exposing confidential data, modifying information, or even deleting critical records. Immediate action is needed to mitigate this vulnerability and ensure the security and integrity of the system.

# No login or authorization is required to exploit this vulnerability
Vulnerability details and POC
## Vulnerability lonameion:
'pagetitle' parameter

<img width="793" alt="屏幕截图 2025-03-30 190804" src="https://github.com/user-attachments/assets/4706372c-8292-4e4f-9416-90e97731402d" />


## payload
<img width="673" alt="屏幕截图 2025-03-30 184705" src="https://github.com/user-attachments/assets/b55811a3-17f3-46a2-ae99-47bece4d1b20" />

## The following are screenshots of some specific information obtained from testing and running with the sqlmap tool:
sqlmap -u "http://0.0.0.0/admin/aboutus.php" --cookie "PHPSESSID=623d6ffa346fe1bd080b26843fc94e54" --data="pagetitle=1&pagedes=2&submit=3" --dbs

<img width="891" alt="屏幕截图 2025-03-30 184815" src="https://github.com/user-attachments/assets/ac253f32-c8fc-4748-ae3c-2cd03cb80130" />


# Suggested repair

## Use Prepared Statements and Parameter Binding:
Utilizing prepared statements with parameter binding is an effective way to prevent SQL injection attacks, as it separates SQL code from user input. When prepared statements are used, user-provided values are treated as raw data, ensuring they cannot be executed as part of the SQL code.

## Input Validation and Sanitization:
It is essential to rigorously validate and sanitize user input to ensure it adheres to the expected format. This step minimizes the risk of malicious data being processed by the system.

## Limit Database User Permissions:
Ensure that the database account used for connections has the minimum required permissions. Avoid using accounts with elevated privileges, such as 'root' or 'admin', for routine database operations.

## Regular Security Audits:
Conduct regular code and system security audits to identify and address potential vulnerabilities in a timely manner. Proactive audits help in maintaining robust system security.
