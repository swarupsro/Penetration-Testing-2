### Port 22 - SSH

- Name:
- Version:
- Protocol:
- RSA-key-fingerprint:
- Takes-password:
If you have usernames test login with username:username

Fingerprint server

    telnet ip_address 22 (banner grab)
    scanssh
        scanssh -p -r -e excludes random(no.)/Network_ID/Subnet_Mask

Password guessing

    ssh root@ip_address
    guess-who
        ./b -l username -h ip_address -p 22 -2 < password_file_location
    Hydra brute force
    brutessh
    Ruby SSH Bruteforcer

Examine configuration files

    ssh_config
    sshd_config
    authorized_keys
    ssh_known_hosts
    .shosts

SSH Client programs

    tunnelier
    winsshd
    putty
    winscp 



nc INSERTIPADDRESS 22
### Other links
https://www.hackingarticles.in/6-ways-to-hack-ssh-login-password/
https://community.turgensec.com/ssh-hacking-guide
https://www.hackingarticles.in/ssh-penetration-testing-port-22/
