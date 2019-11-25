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

Walkthrough
Network Scanning

Let’s start by scanning the network for targets using Netdiscover.

[![ssd](https://1.bp.blogspot.com/-DcAk3IHGRXA/Xc7b0rtZRJI/AAAAAAAAhSQ/bhoJZrb8R6c-oXljraSdlURjJdHmArEAwCLcBGAsYHQ/s1600/1.png "ssd")](https://1.bp.blogspot.com/-DcAk3IHGRXA/Xc7b0rtZRJI/AAAAAAAAhSQ/bhoJZrb8R6c-oXljraSdlURjJdHmArEAwCLcBGAsYHQ/s1600/1.png "ssd")

We found the target IP Address 192.168.1.184. Let’s begin with basic port scanning with NMAP.

[![sd](https://1.bp.blogspot.com/-hdst_cAleL4/Xc7b4SUd7UI/AAAAAAAAhS0/yXZceLS5dQQiAHX1TYDte9CWmVoRNrUbQCLcBGAsYHQ/s1600/2.png "sd")](dsd "sd")
