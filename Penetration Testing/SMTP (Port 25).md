### Port 25 SMTP

- Name:
- Version:
- VRFY:
- EXPN:


https://www.hackingarticles.in/4-ways-smtp-enumeration/


SMTP Enumeration (25):

    nmap –script=smtp-commands,smtp-enum-users,smtp-vuln-cve2010-4344,smtp-vuln-cve2011-1720,smtp-vuln-cve2011-1764 -p 25 10.0.0.1
    nc -nvv INSERTIPADDRESS 25
    telnet INSERTIPADDRESS 25
