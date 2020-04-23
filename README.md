
---

<div align="center">
<a href="https://www.hackthebox.eu/home/users/profile/131282" title="Zer0Code"><img src="https://www.hackthebox.eu/badge/image/131282" alt="alt text" /></a></div>


---

[logo]: Mango.jpg
![alt text](Mango.jpg "Mango")

## NMAP:
As always we will start with NMAP to scan for open ports and services:

```console
# Nmap 7.80 scan initiated Thu Mar  5 18:06:00 2020 as: nmap -p- -sV -sC -O -oN mango_nmap -v 10.10.10.162
RTTVAR has grown to over 2.3 seconds, decreasing to 2.0
Nmap scan report for 10.10.10.162 (10.10.10.162)

```
## HTTP (80) :
* First we checked HTTP service on port 80 and we got forbidden ,also we tried bruteforcing but we got nothing

![alt text](01.png "Mango")

---
## HTTPS (443) :

* We checked HTTPS service and got the same CN that we got with NMAP "staging-order.mango.htb"

![alt text](02.png "Mango")

* so we added “staging-order.mango.htb” to /etc/hosts file and now we got a login page.

![alt text](03.png "Mango")

![alt text](04.png "Mango")

![alt text](05.png "Mango")

* After many trials of login bypass we figured out the meaning of box name hint "Mango" ,so we tried MangoDB Nosql authentication bypass 

![alt text](06.png "Mango")
![alt text](07.png "Mango")

* it worked but nothing interested there

![alt text](08.png "Mango")

* We thought about extracting usernames and passwords from database ,so we used that python script in resources from github

![alt text](09.png "Mango")

* We got two usernames and two passwords

![alt text](10.png "Mango")
![alt text](11.png "Mango")
![alt text](12.png "Mango")

* lets use hydra this time to try creds on SSH and find correct pair 

![alt text](13.png "Mango")

---
## User :

* We used Mango user for connecting to the machine with SSH

![alt text](14.png "Mango")

* User flag with owned by admin ,so we tried to switch to admin user using the other password and it worked 

![alt text](15.png "Mango")

---
## Root :

* First we used simple http server python module to copy linpeas to the machine

![alt text](16.png "Mango")
![alt text](17.png "Mango")

* We found good PE vector using Java jjs 

![alt text](18.png "Mango")

* Using was very clear on gtfobin to read the root flag

![alt text](19.png "Mango")
![alt text](20.png "Mango")

---

## Root Shell :

* For getting root shell we copied our SSH key to authorized keys on the machine using jjs

![alt text](21.png "Mango")

* Now we can connect to the machine using SSH as root

![alt text](22.png "Mango")
















## Resources:

[https://github.com/Zer0CodeX/Nosql-MongoDB-injection-username-password-enumeration](https://github.com/Zer0CodeX/Nosql-MongoDB-injection-username-password-enumeration)

[https://gtfobins.github.io/gtfobins/jjs](https://gtfobins.github.io/gtfobins/jjs)
