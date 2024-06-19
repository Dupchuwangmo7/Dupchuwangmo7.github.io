---
Title: SWS101 CTF Journal
categories: [SWS101, Journal6]
tags: [SWS101]
---
# Valley

Summary

- Enumeration website get hidden directory
- Use creds login ftp –> creds –> user.txt
- Login SSH, analyse binary file -> creds
- Change user –> check cronjob –> python import file –> root.txt

Following are the prove for the steps that I followed.

![alt text](<../images/SWS101-images/CTF Journals/Journal6/Screenshot from 2024-06-19 20-29-48.png>)

Scanning 

![alt text](<../images/SWS101-images/CTF Journals/Journal6/Screenshot from 2024-06-19 20-33-27.png>)

Web Enumeration

![alt text](<../images/SWS101-images/CTF Journals/Journal6/Screenshot from 2024-06-19 20-36-04.png>)

![alt text](<../images/SWS101-images/CTF Journals/Journal6/Screenshot from 2024-06-19 20-37-21.png>)

we can see that a username and password are left in the file

![alt text](<../images/SWS101-images/CTF Journals/Journal6/Screenshot from 2024-06-19 20-40-44.png>)



![alt text](<../images/SWS101-images/CTF Journals/Journal6/Screenshot from 2024-06-19 20-42-18.png>)

Trying to login to FTP with those creditials.

![alt text](<../images/SWS101-images/CTF Journals/Journal6/Screenshot from 2024-06-19 20-46-00.png>)

Using Wireshark to proceed further.

![alt text](<../images/SWS101-images/CTF Journals/Journal6/Screenshot from 2024-06-19 20-49-02.png>)

we got the user.txt

![alt text](<../images/SWS101-images/CTF Journals/Journal6/Screenshot from 2024-06-19 20-52-41.png>)