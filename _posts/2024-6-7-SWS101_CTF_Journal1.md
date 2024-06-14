---
Title: SWS101 CTF Journal
categories: [SWS101, Journal1]
tags: [SWS101]
---

# Bounty Hacker

![alt text](<../images/SWS101-images/CTF Journals/Journal1/Screenshot from 2024-06-09 20-20-55.png>)

![alt text](<../images/SWS101-images/CTF Journals/Journal1/Screenshot from 2024-06-09 20-29-04.png>)

This scan will scan selected top 50 ports to save time and we can see that only 3 ports are open.


Q. Who wrote the task list? 

![alt text](<../images/SWS101-images/CTF Journals/Journal1/Screenshot from 2024-06-09 22-27-13.png>)

we can see that lin has written the note. 

Answer : lin

Q. What service can you bruteforce with the text file found?

There is another text file on the ftp server: locks.txt. It has the following content:

![alt text](<../images/SWS101-images/CTF Journals/Journal1/Screenshot from 2024-06-09 22-31-25.png>)

![alt text](<../images/SWS101-images/CTF Journals/Journal1/Screenshot from 2024-06-09 22-34-14.png>)

Answer : ssh

Q. What is the users password? 

Answer: RedDr4gonSynd1cat3

Q. user.txt

command :  ssh lin@10.10.5.226

Password : RedDr4gonSynd1cat3

![alt text](<../images/SWS101-images/CTF Journals/Journal1/Screenshot from 2024-06-10 16-59-27.png>)

![alt text](<../images/SWS101-images/CTF Journals/Journal1/Screenshot from 2024-06-10 17-04-41.png>)

We got the user.txt i.e THM{CR1M3_SyNd1C4T3}


Q. root.txt

Answer: THM{80UN7Y_h4cK3r}