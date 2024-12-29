# Web Security Testing Guide (WSTG) Project

## Overview
This repository serves as a comprehensive guide and toolkit for implementing and understanding the OWASP Web Security Testing Guide (WSTG). Each section and test case has been meticulously documented to facilitate hands-on learning, testing, and implementation.

The repository is structured around the WSTG categories and test cases. This `README` outlines each section and provides a brief description of the respective testing methodology.

## Table of Contents

### WSTG-INFO | 01 Information Gathering
1. [WSTG-INFO-01: Conduct Search Engine Discovery and Reconnaissance for Information Leakage](WSTG-INFO/WSTG-INFO-01.md)
2. [WSTG-INFO-02: Fingerprint Web Server](WSTG-INFO/WSTG-INFO-02.md)
3. [WSTG-INFO-03: Review Webserver Metafiles for Information Leakage](WSTG-INFO/WSTG-INFO-03.md)
4. [WSTG-INFO-04: Enumerate Applications on Webserver](WSTG-INFO/WSTG-INFO-04.md)
5. [WSTG-INFO-05: Review Application and Webpage Comments for Information Leakage](WSTG-INFO/WSTG-INFO-05.md)
6. [WSTG-INFO-06: Identify Application Entry Points](WSTG-INFO/WSTG-INFO-06.md)
7. [WSTG-INFO-07: Identify Server-Side Technologies](WSTG-INFO/WSTG-INFO-07.md)

### WSTG-CONF | 02 Configuration and Deploy Management Testing
1. [WSTG-CONF-01: Test Network Infrastructure Configuration](WSTG-CONF/WSTG-CONF-01.md)
2. [WSTG-CONF-02: Test Application Platform Configuration](WSTG-CONF/WSTG-CONF-02.md)
3. [WSTG-CONF-03: Test File Extensions Handling for Sensitive Information](WSTG-CONF/WSTG-CONF-03.md)
4. [WSTG-CONF-04: Review HTTP Methods Allowed](WSTG-CONF/WSTG-CONF-04.md)
5. [WSTG-CONF-05: Test HTTP Strict Transport Security](WSTG-CONF/WSTG-CONF-05.md)
6. [WSTG-CONF-06: Test RIA Cross Domain Policy](WSTG-CONF/WSTG-CONF-06.md)
7. [WSTG-CONF-07: Test File Permissions](WSTG-CONF/WSTG-CONF-07.md)
8. [WSTG-CONF-08: Test for Subdomain Takeover](WSTG-CONF/WSTG-CONF-08.md)
9. [WSTG-CONF-09: Test Cloud Storage Permissions](WSTG-CONF/WSTG-CONF-09.md)
10. [WSTG-CONF-10: Test Administrative Interfaces](WSTG-CONF/WSTG-CONF-10.md)
11. [WSTG-CONF-11: Test for Security Headers](WSTG-CONF/WSTG-CONF-11.md)


### 3. Identity Management Testing
Tests related to identity management and user account controls.

- **WSTG-IDNT-01**: Test Role Definitions
- **WSTG-IDNT-02**: Test User Registration Process
- **WSTG-IDNT-03**: Test Account Provisioning Process
- **WSTG-IDNT-04**: Testing for Account Enumeration and Guessable User Account
- **WSTG-IDNT-05**: Testing for Weak or Unenforced Username Policy

### 4. Authentication Testing
Testing authentication mechanisms for security vulnerabilities.

- **WSTG-ATHN-01**: Testing for Credentials Transported over an Encrypted Channel
- **WSTG-ATHN-02**: Testing for Default Credentials
- **WSTG-ATHN-03**: Testing for Weak Lock Out Mechanism
- **WSTG-ATHN-04**: Testing for Bypassing Authentication Schema
- **WSTG-ATHN-05**: Testing for Vulnerable Remember Password
- **WSTG-ATHN-06**: Testing for Browser Cache Weakness
- **WSTG-ATHN-07**: Testing for Weak Password Policy
- **WSTG-ATHN-08**: Testing for Weak Security Question Answer
- **WSTG-ATHN-09**: Testing for Weak Password Change or Reset Functionalities
- **WSTG-ATHN-10**: Testing for Weaker Authentication in Alternative Channel

### 5. Authorization Testing
Analyzing authorization controls to ensure robust security.

- **WSTG-ATHZ-01**: Testing Directory Traversal File Include
- **WSTG-ATHZ-02**: Testing for Bypassing Authorization Schema
- **WSTG-ATHZ-03**: Testing for Privilege Escalation
- **WSTG-ATHZ-04**: Testing for Insecure Direct Object References

### 6. Session Management Testing
Evaluating session management mechanisms.

- **WSTG-SESS-01**: Testing for Session Management Schema
- **WSTG-SESS-02**: Testing for Cookies Attributes
- **WSTG-SESS-03**: Testing for Session Fixation
- **WSTG-SESS-04**: Testing for Exposed Session Variables
- **WSTG-SESS-05**: Testing for Cross Site Request Forgery
- **WSTG-SESS-06**: Testing for Logout Functionality
- **WSTG-SESS-07**: Testing Session Timeout
- **WSTG-SESS-08**: Testing for Session Puzzling
- **WSTG-SESS-09**: Testing for Session Hijacking
- **WSTG-SESS-10**: Testing JSON Web Tokens

### 7. Input Validation Testing
Ensuring proper input validation to prevent attacks.

- **WSTG-INPV-01**: Testing for Reflected Cross Site Scripting
- **WSTG-INPV-02**: Testing for Stored Cross Site Scripting
- **WSTG-INPV-03**: Testing for HTTP Verb Tampering
- **WSTG-INPV-04**: Testing for HTTP Parameter Pollution
- **WSTG-INPV-05**: Testing for SQL Injection

### 8. Error Handling
Analyzing application error handling mechanisms.

- **WSTG-ERRH-01**: Testing for Improper Error Handling
- **WSTG-ERRH-02**: Testing for Stack Traces

### 9. Cryptography
Assessing cryptographic implementations.

- **WSTG-CRYP-01**: Testing for Weak Transport Layer Security
- **WSTG-CRYP-02**: Testing for Padding Oracle

### 10. Business Logic Testing
Testing business logic implementation.

- **WSTG-BUSL-01**: Test Business Logic Data Validation
- **WSTG-BUSL-02**: Test Ability to Forge Requests

### 11. Client-Side Testing
Reviewing client-side code and functionality.

- **WSTG-CLNT-01**: Testing for DOM Based Cross Site Scripting
- **WSTG-CLNT-02**: Testing for JavaScript Execution

### 12. API Testing
Specialized tests for APIs.

- **WSTG-APIT-01**: Testing GraphQL

---

## Contributions
Feel free to open issues or create pull requests to contribute to this project.

## License
This repository is licensed under the [MIT License](LICENSE).
