# DVWA Web Application Security Assessment

## Overview

This project presents a hands-on security assessment of **Damn Vulnerable Web Application (DVWA)**, an intentionally vulnerable web application designed for security training and practice.

The assessment was performed in a controlled local lab environment using **Kali Linux, Firefox, Burp Suite, Apache, PHP, and MariaDB**.

The project focused on identifying and demonstrating four assigned web application vulnerabilities:

- Login Bypass / Brute Force
- SQL Injection — Admin Credentials Access
- Cross-Site Request Forgery (CSRF)
- Cross-Site Scripting (XSS)

The assessment included manual testing, Burp Suite testing, source-code review, proof-of-concept validation, and analysis of security impact and mitigation techniques.

---

## Project Objectives

The objectives of this project were to:

- Identify and understand the four assigned vulnerabilities.
- Validate the vulnerabilities through manual testing.
- Use Burp Suite to intercept and analyze application traffic.
- Review relevant application source code to understand the underlying weaknesses.
- Demonstrate proof-of-concept exploitation in a controlled DVWA environment.
- Document the testing process and supporting evidence.
- Analyze the potential security impact of each vulnerability.
- Identify appropriate security controls and mitigation techniques.

---

## Target Application

### Damn Vulnerable Web Application (DVWA)

DVWA is an intentionally vulnerable PHP/MariaDB web application designed for learning and practicing web application security.

The application was deployed locally and tested within the controlled lab environment.

**Target:** DVWA  
**Environment:** Localhost  
**Application Stack:** PHP / MariaDB  
**Purpose:** Web application security training and vulnerability testing

---

## Lab Environment

| Component | Details |
|---|---|
| Operating System | Kali Linux |
| Browser | Firefox |
| Web Server | Apache 2.4.62 |
| Server-Side Language | PHP 8.2.21 |
| Database | MariaDB 11.4.2 |
| Target Application | DVWA |
| DVWA Security Level | Medium for the primary assessment |

Supporting evidence from DVWA Low security level testing is also included in the project material.

---

# Vulnerabilities Tested

## 1. Login Bypass / Brute Force

### OWASP Classification

**A07:2021 — Identification and Authentication Failures**

### Description

A brute-force attack attempts multiple username and password combinations in order to discover valid authentication credentials.

The DVWA authentication functionality was tested to understand how repeated authentication attempts could be used to identify valid credentials.

### Testing

Testing was performed using:

- DVWA
- Burp Suite Intruder
- Candidate username wordlist
- Candidate password wordlist

The assessment included testing multiple username and password combinations and analyzing responses to identify successful authentication.

### Medium-Level Testing

The Medium security implementation was examined to understand the additional delay introduced during failed authentication attempts.

Burp Suite Intruder was used to automate the testing and analyze the resulting responses.

### Evidence

Supporting evidence includes:

- Login request interception
- Intruder configuration
- Payload positions
- Username and password wordlists
- Intruder attack results
- Successful authentication
- Medium-level delay behavior

---

# 2. SQL Injection — Admin Credentials Access

### OWASP Classification

**A03:2021 — Injection**

### Description

SQL Injection occurs when user-controlled input is incorporated into SQL queries without adequate protection, allowing an attacker to manipulate the query and potentially access unauthorized database information.

The SQL Injection functionality in DVWA was tested to understand how database queries could be manipulated.

### Testing

Testing was performed using:

- DVWA
- Burp Suite Repeater
- Manual SQL Injection testing
- Response analysis
- Hash extraction and analysis

The project covered multiple SQL Injection techniques, including:

- Error-based SQL Injection
- Union-based SQL Injection
- Blind Boolean-based SQL Injection
- Blind Time-based SQL Injection

### Testing Evidence

The project contains evidence showing:

- Normal SQL query behavior
- SQL Injection responses
- Error-based testing
- Union-based testing
- Boolean-based blind SQL Injection
- Time-based blind SQL Injection
- Burp Suite request interception
- Burp Suite Repeater testing
- Database information retrieval
- Password hash extraction
- Hash lookup analysis

---

# 3. Cross-Site Request Forgery (CSRF)

### OWASP Classification

**A01:2021 — Broken Access Control**

### Description

Cross-Site Request Forgery (CSRF) occurs when an attacker causes an authenticated user's browser to send an unwanted request to a web application.

The DVWA password-change functionality was tested to demonstrate how a crafted request could cause an authenticated action without the user's intended interaction.

### Testing

Testing was performed using:

- DVWA
- Burp Suite
- Burp Suite Repeater
- CSRF proof-of-concept request
- Local HTTP server for the testing workflow

### Demonstration

The assessment included:

- Capturing the relevant request
- Analyzing the request parameters
- Generating a CSRF proof of concept
- Opening the generated request in a browser
- Testing the request while authenticated
- Observing the resulting password-change behavior

### Evidence

Supporting evidence includes:

- CSRF input
- Captured requests
- Burp Suite request interception
- CSRF proof-of-concept
- Local HTTP server
- Authentication state
- Password-change result

---

# 4. Cross-Site Scripting (XSS)

### OWASP Classification

**A03:2021 — Injection**

### Description

Cross-Site Scripting (XSS) occurs when untrusted input is improperly handled, allowing attacker-controlled JavaScript to execute in a user's browser.

The project investigated multiple forms of XSS within DVWA.

### XSS Types Tested

- Stored XSS
- Reflected XSS
- DOM-Based XSS

### Testing

Testing was performed using:

- DVWA
- Burp Suite Repeater
- Burp Suite
- DOM Invader
- Browser-based testing

The assessment included submitting crafted input and observing JavaScript execution in the browser.

### Evidence

Supporting evidence includes:

- Reflected XSS input
- Reflected XSS execution
- Stored XSS input
- Stored XSS execution
- DOM XSS testing
- Burp Suite request interception
- Burp Suite XSS testing
- DOM Invader analysis

---

# Source-Code Analysis

Relevant DVWA source-code screenshots were reviewed for the vulnerabilities tested during the project.

The project material contains source-code evidence for:

- Brute Force
- CSRF
- SQL Injection
- XSS

The source-code review was used to understand the application logic, security controls, and weaknesses associated with the tested functionality.

Source-code evidence includes multiple DVWA security levels, including Low, Medium, High, and Impossible where available in the project material.

---

# Testing Methodology

The project followed a structured web application security testing process:

1. Set up DVWA in a local controlled environment.
2. Configure the required Apache and MariaDB services.
3. Access and configure the DVWA application.
4. Perform initial reconnaissance of the application.
5. Identify the functionality associated with each assigned vulnerability.
6. Review the relevant application source code.
7. Perform manual vulnerability testing.
8. Use Burp Suite to intercept and analyze HTTP requests.
9. Use Burp Suite tools such as Repeater and Intruder where applicable.
10. Validate the observed behavior through proof-of-concept testing.
11. Capture screenshots and supporting evidence.
12. Analyze the security impact of each vulnerability.
13. Identify appropriate security mitigations.

---

# Reconnaissance

Initial reconnaissance was performed against the local DVWA environment to understand the application and its HTTP behavior.

The reconnaissance evidence includes:

- Passive reconnaissance
- Active reconnaissance
- HTTP response/header analysis

The reconnaissance stage helped establish an understanding of the target application before performing vulnerability-specific testing.

---

# Tools Used

### Burp Suite

Burp Suite was used extensively during the assessment for:

- HTTP request interception
- Request analysis
- Request modification
- Manual testing with Repeater
- Automated testing with Intruder
- XSS testing
- CSRF proof-of-concept generation
- Traffic analysis

### CrackStation

CrackStation was used for hash lookup during the SQL Injection investigation to assist with analysis of an extracted password hash.

### Kali Linux

Kali Linux was used as the primary security testing environment.

### Apache

Apache was used as the web server hosting the local DVWA application.

### MariaDB

MariaDB was used as the database backend for DVWA.

---

# Security Impact

The assessment demonstrated security risks associated with:

- Authentication and credential security
- Database security
- Unauthorized access to application data
- Unauthorized user actions
- Client-side script execution
- Improper input handling
- Insufficient request validation
- Inadequate security controls

The project demonstrated how weaknesses in authentication, database queries, request validation, and output handling can affect web application security.

---

# Recommendations & Mitigations

## Login Bypass / Brute Force

Recommended controls include:

- Login throttling and rate limiting
- Account lockout or protective controls after repeated failures
- Multi-factor authentication (MFA)
- Monitoring and logging of failed login attempts
- Strong password policies

---

## SQL Injection

Recommended controls include:

- Parameterized queries
- Prepared statements
- Appropriate allow-list input validation
- Least-privilege database accounts
- Web Application Firewall (WAF) as a defense-in-depth control

---

## CSRF

Recommended controls include:

- Unpredictable CSRF tokens
- SameSite cookie controls
- Origin/Referer validation
- Re-authentication for sensitive actions

---

## XSS

Recommended controls include:

- Context-aware output encoding
- Safe DOM APIs
- Appropriate input validation
- Content Security Policy (CSP)
- Avoiding blacklist-only filtering

---

# Key Learning Outcomes

This project provided practical experience with:

- Web application security assessment
- Vulnerability identification
- Manual security testing
- Burp Suite
- HTTP request and response analysis
- SQL Injection
- Blind SQL Injection
- Cross-Site Scripting
- DOM-Based XSS
- Cross-Site Request Forgery
- Brute-force authentication testing
- Source-code review
- Reconnaissance
- Proof-of-concept validation
- Security impact analysis
- Vulnerability mitigation

---

# Conclusion

Four assigned web application vulnerabilities were investigated and demonstrated in the DVWA environment:

1. Login Bypass / Brute Force
2. SQL Injection — Admin Credentials Access
3. Cross-Site Request Forgery (CSRF)
4. Cross-Site Scripting (XSS)

Manual testing, source-code review, and Burp Suite were used to validate the findings.

The assessment demonstrated security risks affecting authentication, database security, user actions, and client-side application security.

The project also provided practical experience in vulnerability testing, HTTP traffic analysis, source-code review, proof-of-concept development, and security mitigation.

---

# References

- OWASP Top 10:2021
- OWASP Web Security Testing Guide (WSTG)
- Damn Vulnerable Web Application (DVWA)
- PortSwigger Burp Suite Documentation
- SecLists
- CrackStation
- HackerDNA
