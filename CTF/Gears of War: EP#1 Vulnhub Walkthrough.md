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
