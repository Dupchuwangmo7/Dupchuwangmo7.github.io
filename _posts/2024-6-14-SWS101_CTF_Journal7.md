---
Title: SWS101 CTF Journal
categories: [SWS101, Journal7]
tags: [SWS101]
---

# CyberHeroes

First, we will check for website. 

![alt text](<../images/SWS101-images/CTF Journals/Journal7/Screenshot from 2024-06-20 01-51-38.png>)

And we are going to view thw page source.

![alt text](<../images/SWS101-images/CTF Journals/Journal7/Screenshot from 2024-06-20 01-56-31.png>)

I found that a function called authenticate() is called on Button Click. And it has the function of 

![alt text](<../images/SWS101-images/CTF Journals/Journal7/Screenshot from 2024-06-20 01-59-34.png>)

The script has given us following information:
- String = 54321@terceSrepuS
- Value = h3ck3rBoi

Now we got string which uses a ReverseString Function so Let’s try to Reverse it.

![alt text](<../images/SWS101-images/CTF Journals/Journal7/Screenshot from 2024-06-20 02-02-59.png>)

so, our password is SuperSecret@12345 and username is h3ck3rBoi.

![alt text](<../images/SWS101-images/CTF Journals/Journal7/Screenshot from 2024-06-20 02-05-23.png>)

And we got the flag and we are done with the machine.