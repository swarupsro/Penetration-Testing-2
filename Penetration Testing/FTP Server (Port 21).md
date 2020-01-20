### Port 21 - FTP
    Name:
    Version:
    Anonymous login:
    Fingerprint server
        telnet ip_address 21 (Banner grab)
        Run command ftp ip_address
        ftp@example.com
        Check for anonymous access
            ftp ip_addressUsername: anonymous OR anonPassword: any@email.com
    Password guessing
        Hydra brute force
        medusa
        Brutus
    Examine configuration files
        ftpusers
        ftp.conf
        proftpd.conf
    MiTM
        pasvagg.pl 



```
nmap –script=ftp-anon,ftp-bounce,ftp-libopie,ftp-proftpd-backdoor,ftp-vsftpd-backdoor,ftp-vuln-cve2010-4221,tftp-enum -p 21 10.0.0.1
```
#### Other links
https://medium.com/p/19afe538be4b

https://www.hackingarticles.in/6-ways-to-hack-ftp-login-password/

