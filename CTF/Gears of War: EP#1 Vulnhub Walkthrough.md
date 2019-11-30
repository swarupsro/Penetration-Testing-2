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

    > netdiscover

[![ssd](https://1.bp.blogspot.com/-DcAk3IHGRXA/Xc7b0rtZRJI/AAAAAAAAhSQ/bhoJZrb8R6c-oXljraSdlURjJdHmArEAwCLcBGAsYHQ/s1600/1.png "ssd")](https://1.bp.blogspot.com/-DcAk3IHGRXA/Xc7b0rtZRJI/AAAAAAAAhSQ/bhoJZrb8R6c-oXljraSdlURjJdHmArEAwCLcBGAsYHQ/s1600/1.png "ssd")

We found the target IP Address 192.168.1.184. Let’s begin with basic port scanning with NMAP.

    > nmap -A -p- 192.168.1.184

[![sd](https://1.bp.blogspot.com/-hdst_cAleL4/Xc7b4SUd7UI/AAAAAAAAhS0/yXZceLS5dQQiAHX1TYDte9CWmVoRNrUbQCLcBGAsYHQ/s1600/2.png "sd")](dsd "sd")

Enumeration

For more details, we will need to start enumeration against the host machine. Therefore, we will navigate to a web browser for exploring HTTP service since port 80 is open.

[![sd](https://1.bp.blogspot.com/-tWvJslaFjsQ/Xc7b5eDeoYI/AAAAAAAAhS8/FSbB4GRc9xkZ73iIZ83Cj9Bog2xupYiJQCLcBGAsYHQ/s1600/3.png "sd")](dsd "sd")

Since HTTP service was not much of a help. On the other hand, we can clearly note from the nmap scan that we have the SMB service running, and we don’t have any credentials for the ssh so we went directly on with SMB. We logged in using the command mentioned. There is a list of shared directories. We tried accessing LOCUS_LAN$ directory and enumerated it. We find a notes.txt file and msg_horda.zip file. Let’s transfer these files on our machine to read their contents.

    > smbclient -L 192.168.1.184
    > smbclient //192.168.1.184/LOCUS_LAN$
    > get msg_horda.zip
    > get SOS.txt
    > ls

[![sd](https://1.bp.blogspot.com/-OlJOMed9xTA/Xc7b4_swmVI/AAAAAAAAhS4/dbZTrs4hnqEW5b8yFy-xGBEmkGlEjsEwQCLcBGAsYHQ/s1600/4.png "sd")](dsd "sd")

We tried opening the msg_horda.zip file but it seems password protected.

[![sd](https://1.bp.blogspot.com/-KWdpchB7rSY/Xc7b5Y2-1AI/AAAAAAAAhTA/pDq-3riNfFEkeGe7sPY9-ROzX-mHhC79ACLcBGAsYHQ/s1600/5.png"sd")](dsd "sd")

We thought of reading the contents of SOS.txt file and it was a success. It surely gave us a hint about the characters of the password for ZIP file.

[![sd](https://1.bp.blogspot.com/-ZzR4MrfHwK0/Xc7b59xPQUI/AAAAAAAAhTE/uUc5Jd8iWz8JlNqyNs0Y-XdD52bETAmVwCLcBGAsYHQ/s1600/6.png"sd")](dsd "sd")

#### Exploiting
It’s time to FIRE UP!! Crunch and generate a wordlist as per the combination of the password we have fetched from the SOS.txt file.

    > crunch 4 4 -t @%%, -o wordlist

[![sd](https://1.bp.blogspot.com/-urR3hwnlwMU/Xc7b6FH5UUI/AAAAAAAAhTI/C_xhBS2aUgE6e1RQg9aMZsg6mvy_bRRUwCLcBGAsYHQ/s1600/7.png"sd")](dsd "sd")

Once the wordlist is all set up, we have used FCRACK TOOL to crack the password for the ZIP file as shown below.
	
    > frackzip -D -u -v -p wordlist msg_horda.zip

The password for the ZIP file is r44M. We also found a key.txt file inside the ZIP file.

[![sd](https://1.bp.blogspot.com/-ogQ7qeATPvQ/Xc7b6vpnxCI/AAAAAAAAhTM/rAVhnmygTssP3-ajnnzbJfyzFCvC5QamwCLcBGAsYHQ/s1600/8.png"sd")](dsd "sd")

After reading the key.txt file, we got another credential which could be useful for SSH login but we still need a username. Bring up HYDRA.

[![sd](https://1.bp.blogspot.com/-W_keq5u6aZ8/Xc7b6u38E5I/AAAAAAAAhTQ/0QR-4SrmnjgFTGtxqVaZlchGpoKzBtcOQCLcBGAsYHQ/s1600/9.png"sd")](dsd "sd")

We have brute forced the username for SSh Login using hydra with password 3_d4y.

    > hydra -L /usr/share/wordlists/rockyou.txt -p 3_d4y -T4 192.168.1.184 ssh

[![sd](https://1.bp.blogspot.com/-xjMDA1maMm0/Xc7b0dO7WBI/AAAAAAAAhSM/C-K-4sHEu9c2Uo6lMIOXcrjOJ921Il0EwCLcBGAsYHQ/s1600/10.png"sd")](dsd "sd")

After successfully logged into SSH, we try enumerating the /etc directory but couldn’t because user Marcus doesn’t have the privileges to access the /etc directory.

    > ssh marcus@192.168.1.184
    > id
    > cd /etc

[![sd](https://1.bp.blogspot.com/-vsPL5WcJvrE/Xc7b0gSqo-I/AAAAAAAAhSU/dbgsnZxSSz0Wp1sjbFPMUJjj7RG7ppLQACLcBGAsYHQ/s1600/11.png"sd")](dsd "sd")

#### Privilege Escalation

Since our target machine is in a bash shell. We will be using a command to force SSH for TTY allocation. This will help us run commands as an administrator. Finally, we are able to access the /etc directory.

    > ssh marcus@192.168.1.184 -t "bash --noprofile"
    > cd /etc

[![sd](https://1.bp.blogspot.com/-l5cRxRFZZBk/Xc7b1vKx3tI/AAAAAAAAhSc/jDwVyX5WjkolLAmKK-c-KkXIUxq5KNE5wCLcBGAsYHQ/s1600/12.png"sd")](dsd "sd")

    > pwd

On reading the passwd file which was not much help, but we got an idea what we can do next.

    > cat passwd

[![sd](https://1.bp.blogspot.com/-22sFp0mQPrQ/Xc7b1r2ljkI/AAAAAAAAhSY/9qbRH85twUIa_gBA5uoeR3krAKgCpELggCLcBGAsYHQ/s1600/13.png"sd")](dsd "sd")

On checking the SUID bit for all the readable files under /bin directory, we came to know that the current user can use the cp command. This is going to be interesting.

    > find /bin -type f -perm -u=s 2>/dev/null

[![sd](https://1.bp.blogspot.com/-g7msejnGThQ/Xc7b17b_2fI/AAAAAAAAhSg/yYrC3H0bYXMUeiksVIGoCGT4VCPalhKYQCLcBGAsYHQ/s1600/14.png"sd")](dsd "sd")

Without any further waiting, we need the password hash for the user that we are going to create on the target machine by making an entry in the /etc/passwd file. We are going to use the openssl to generate a salted hash.

    > openssl passwd -1 -salt raj pass123

[![sd](https://1.bp.blogspot.com/-ZFTFm7ri0U4/Xc7b2Y655MI/AAAAAAAAhSk/ioLBv5LhNxQA81k_5_hf53n7li_8guJhgCLcBGAsYHQ/s1600/15.png"sd")](dsd "sd")

Now back to our user marcus on the target machine. Here we are going to use the hash that we generated in the previous step and make a user raj which has the elevated privilege. We have to use nano command to make an entry in the /tmp directory. After making an entry we checked the entry using the tail command. cd /tmp

    > nano passwd
    > cat passwd | tail

[![sd](https://1.bp.blogspot.com/-8iBIRQ-XWbA/Xc7b3Ei8srI/AAAAAAAAhSo/H4XZjcTY02EroXH0tyx3Z58jdxjP4FwTQCLcBGAsYHQ/s1600/16.png"sd")](dsd "sd")

Now all we to do login using username and password, we just created to get our root shell. On enumeration we found flag.txt.

    > su raj
    > whoami
    > cd /root
    > ls -al

[![sd](https://1.bp.blogspot.com/-RJhHbIqOtzg/Xc7b3Arc5TI/AAAAAAAAhSs/9yGBimFr1zscW6Wz0fA6zDEZUO5i6CH8gCLcBGAsYHQ/s1600/17.png"sd")](dsd "sd")

Time to Read our Final Flag!!

    > cat flag.txt

[![sd](https://1.bp.blogspot.com/-teZD-XEdADA/Xc7b3UoPuHI/AAAAAAAAhSw/JxtEDptUjjkAl5i11WCxuQFb-CSByZIbQCLcBGAsYHQ/s1600/18.png"sd")](dsd "sd")
