## Gears of War: EP#1 Vulnhub Walkthrough
Gears of War: EP#1 VM is made by eDu809. This VM is a purposely built vulnerable lab with the intent of gaining experience in the world of penetration testing. It is of intermediate level and is very handy in order to brush up your skills as a penetration tester. The ultimate goal of this challenge is to get root and to read the root flag.

Level: Intermediate

Since these labs are available on the Vulnhub Website. We will be downloading the lab file from this [link](https://www.vulnhub.com/entry/gears-of-war-ep1,382/).
Penetration Testing Methodology

Network Scanning

    Netdiscover
    Nmap Port Scan

Enumeration

    Browsing HTTP Service
    SMB Login

Exploiting

    Using Crunch to generate a wordlist
    Using Fcrack to bruteforce ZIP file password
    Using Hydra to bruteforce SSH Login

Privilege Escalation

    Reading /etc/passwd File
    Getting SUID bit files
    Using Openssl for generating a password hash
    Adding  User to /tmp file
    Reading Final Flag

### Walkthrough
##### Network Scanning

Let’s start by scanning the network for targets using Netdiscover.

[![ssd](https://1.bp.blogspot.com/-DcAk3IHGRXA/Xc7b0rtZRJI/AAAAAAAAhSQ/bhoJZrb8R6c-oXljraSdlURjJdHmArEAwCLcBGAsYHQ/s1600/1.png "ssd")](https://1.bp.blogspot.com/-DcAk3IHGRXA/Xc7b0rtZRJI/AAAAAAAAhSQ/bhoJZrb8R6c-oXljraSdlURjJdHmArEAwCLcBGAsYHQ/s1600/1.png "ssd")

We found the target IP Address 192.168.1.184. Let’s begin with basic port scanning with NMAP.

[![sd](https://1.bp.blogspot.com/-hdst_cAleL4/Xc7b4SUd7UI/AAAAAAAAhS0/yXZceLS5dQQiAHX1TYDte9CWmVoRNrUbQCLcBGAsYHQ/s1600/2.png "sd")](dsd "sd")

Enumeration

For more details, we will need to start enumeration against the host machine. Therefore, we will navigate to a web browser for exploring HTTP service since port 80 is open.

[![sd](https://1.bp.blogspot.com/-tWvJslaFjsQ/Xc7b5eDeoYI/AAAAAAAAhS8/FSbB4GRc9xkZ73iIZ83Cj9Bog2xupYiJQCLcBGAsYHQ/s1600/3.png "sd")](dsd "sd")

Since HTTP service was not much of a help. On the other hand, we can clearly note from the nmap scan that we have the SMB service running, and we don’t have any credentials for the ssh so we went directly on with SMB. We logged in using the command mentioned. There is a list of shared directories. We tried accessing LOCUS_LAN$ directory and enumerated it. We find a notes.txt file and msg_horda.zip file. Let’s transfer these files on our machine to read their contents.

[![sd](https://1.bp.blogspot.com/-OlJOMed9xTA/Xc7b4_swmVI/AAAAAAAAhS4/dbZTrs4hnqEW5b8yFy-xGBEmkGlEjsEwQCLcBGAsYHQ/s1600/4.png "sd")](dsd "sd")

We tried opening the msg_horda.zip file but it seems password protected.

[![sd](https://1.bp.blogspot.com/-KWdpchB7rSY/Xc7b5Y2-1AI/AAAAAAAAhTA/pDq-3riNfFEkeGe7sPY9-ROzX-mHhC79ACLcBGAsYHQ/s1600/5.png"sd")](dsd "sd")

We thought of reading the contents of SOS.txt file and it was a success. It surely gave us a hint about the characters of the password for ZIP file.

[![sd](https://1.bp.blogspot.com/-ZzR4MrfHwK0/Xc7b59xPQUI/AAAAAAAAhTE/uUc5Jd8iWz8JlNqyNs0Y-XdD52bETAmVwCLcBGAsYHQ/s1600/6.png"sd")](dsd "sd")

#### Exploiting
It’s time to FIRE UP!! Crunch and generate a wordlist as per the combination of the password we have fetched from the SOS.txt file.

[![sd](https://1.bp.blogspot.com/-urR3hwnlwMU/Xc7b6FH5UUI/AAAAAAAAhTI/C_xhBS2aUgE6e1RQg9aMZsg6mvy_bRRUwCLcBGAsYHQ/s1600/7.png"sd")](dsd "sd")
