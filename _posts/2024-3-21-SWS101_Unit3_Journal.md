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



