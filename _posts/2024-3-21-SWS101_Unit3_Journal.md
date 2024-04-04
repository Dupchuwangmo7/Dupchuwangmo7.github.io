---
Title: SWS101 Unit 3 Journal
categories: [SWS101, Journal4]
tags: [SWS101]
---

# Introduction
For unit 3 journal, we have go through Try Hack Me room OWASP Top 10-2021. In this room, we are going to learn about OWASP topicthat includes details on the vulnerabilities,how they occur and how we can exploit them. We have to put theory into practical by completing supporting challenges.

The OWASP topic includes:
1. Broken Access Control
2. Crytographic Failures
3. Injection
4. Insecure Design
5. Security Misconfiguration
6. Valuerable and Outdated components
7. Identification and Authentication Failures
8. Software and Data Integrity failures
9. Security Logging and Monitoring Failures
10. Server-Side Request Forgery(SSRF)

### Accessing Machines
We are going to access these machines by connecting with OpenVPN. To do that we have to download the vpn file and connect it through terminal.


    sudo openvpn file-path

## 1. Broken Access Control

Broken Access control is a common and critical security vulnerability that arises when access control mechanisms are waek, improperly implemented or not enforced effectively. This allows unauthorized or regular users to gain access to sensitive data, system or functionalities.It also  occurs when an application fails to properly enforce access controls, allowing attackers to bypass authorization and perform tasks as if they were a legitimate user.


#### Insecure Direct Object reference
It is a specific type of Broken Access Control vulnerability. It occurs when an application uses user-supplied input to directly access object without proper authorization checks. This allows attackers to manipulates references and gain unauthorized access to resourse. Impacts of IDOR are Data Breaches and Unauthorized Actions. 
Data breaches is when attackers can access sensitive data of other users, leading to privacy breaches or identity theft. And unauthorized action is when attacker are able to perform actions they shouldn't be allowed to on someone else's account.

## 2. Crytographic Failures
It is a security vulnerabilities that arise when system don't safegurad sensitive data using crytography effectively. It can also arise from the misuse of crytographic alogrithms for protecting sensitive information. 

An example for crytographic failure is The Heartbleed bug(2014). It was serious flaw in OpenSSL, encryption software that powers a lot of secure communicaton on the web. The SSL standard includes a heartbeat option, which allows a computer at one end of an SSL connection to send a short message to verify that the other computer is still online and get a response back. Researchers found that it's possible to send a cleverly formed, malicious heartbeat message that tricks the computer at the other end into divulging secret information. Specifically, a vulnerable computer can be tricked into transmitting the contents of the server's memory, known as RAM. lots of company such as Google, Tumblr, Dropbox, Netflix, Yahoo and Facebook were affected by this bug.

Crytographic failure often end up in web apps accidentally divulging sensitive data. The data can be broadly categorized into two main areas, that is Customer Data and Technical Information. Under Customer data, it includes information that can be used to identity a specific individual and financial information. This kind of exposure can cause severe consequence for both the customer and the wen organization. Another one is exposure of technical information which includes username and password where attacker can hijack account and steal further data, API keys and Access Tokens where attacker can gain unauthorized access to sensitive data or functionalities.

In Crytographic failure(Supporting Material 2) we are introduced to new online tool called Crackstation. This tool is  used craking weak password hashes. 

## 3. Injection

![alt text](<../images/SWS101-images/OWASP _Top_10/Screenshot from 2024-04-03 01-19-02.png>)

Injection attacks are a common and dangerous type os cyberattack that exploit vulnerabilities in the how application handles user input. It occurs when an attacker inserts malicious code into input field on a web form, this code can then be executed by the application, potentially leading to a variety of negative consequences.

#### How it works
1. Vulnerable Application: The web appication has a form where users can input data.
2. Malicious Input: An attacker crafts a specially crafted input containing mailicious code.
3. Insufficient Vaildation: The application fails to properly vaildate and sanitize the user input before using it.
4. Code Execution: The mailicious code gets injected into the application's backend and executes.

Some common example of Injection attack:
- SQL Injection
    - targets database.
    - Injected code can steal sensitive data, modify database, or even take control of the database server.
- Command Injection
    - Targets the operating system of the server.
    - Injected code can execute arbitary commands on the server, potentially giving attacker full control.
- Cross-Site Scripting (XSS)
    - Targets the web browser.
    - Injected code can steal session cookies, redirect users to malicious websites, or deface web pages.
- LDAP Injection
    - Targets Lightweight Directory Access Protocol (LDAP) server used for authentication.
    - Attackers can steal user credentials or disrupt disrupt directory services.

Impacts of Injection Attacks
- Data Breaches: attcker can steal sensitive information.

- Website Defacement: attackers can modify the content of a websites to display malicious content.

- System Takeover: attcker can gain complete control of the underlying system.

Prevention for Injection Attacks
- Input validation and Sanitization
- Parameterized Queries: used it to seperate data from database commands, preventing SQLi attacks.
- Escape User Input
- Regular Security Updates

### 3.1 Command Injection

Command Injection occurs when server-side code in a web application makes a call to a function that interacts with the server's console directly. 

In this machine, we will complete cowsay challenge using linux commands. Common Basic commands are:
- whoami
- id
- ifconfig/ip addr
- uname -a
- ps -ef

But in this machine we will use
- $(ls)
- $(ls -la)
- $(cat /etc/passwd)
- $(cat /etc/os-release)

Answers for the Questions

Question 1

![alt text](<../images/SWS101-images/OWASP _Top_10/Screenshot from 2024-04-03 01-08-50.png>)

Question 2

![alt text](<../images/SWS101-images/OWASP _Top_10/Screenshot from 2024-04-03 01-11-41.png>)
 
Question 3 

 ![alt text](<../images/SWS101-images/OWASP _Top_10/Screenshot from 2024-04-03 01-00-39.png>)

 Question 4

 ![alt text](<../images/SWS101-images/OWASP _Top_10/Screenshot from 2024-04-03 01-14-40.png>)

 Question 5

 ![alt text](<../images/SWS101-images/OWASP _Top_10/Screenshot from 2024-04-03 01-16-01.png>)


## 4. Insecure Design
