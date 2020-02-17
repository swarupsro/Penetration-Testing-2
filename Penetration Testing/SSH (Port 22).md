### Port 22 - SSH

SSH keys

So, whilst looking around the file system and looking for passwords in the various shell histories and standard scripts, I noticed that one user, let’s call it batchuser, had an SSH keypair defined; implying that it had been used to connect to other servers.

A bit of background: SSH can support a number of different authentication mechanisms, from the basic password to using keys. SSH keys follow conventional asymmetric authentication schemes: a keypair, consisting of a public and private key, is generated (saved, by default in the .ssh/id_rsa and .ssh/id-rsa.pub files on the client) and the public key is sent to the destination host. When the client tries to authenticate it signs the request with the private key and the server verifies with its copy of the public key and decides whether to give access.

All this is set up in files in the user’s .ssh directory, with authorised keys saved in the .ssh/authorized_keys file on the server.

So I found some keys, that doesn’t tell me which servers the user has access to does it? No, not really. Now I could farm through the shell histories or looks at the scripts, or I could just be lazy and use another facility of the SSH protocol.
Host keys

Each SSH server has its own key and signature which it presents upon initial connection by a client. This is an extra integrity step to minimise the risk of man-in-the-middle attacks. Once the host key has been accepted its signature is saved in .ssh/known_hosts on the client.

This means that we would have, at least the following files on the server

    .ssh/authorized_keys – holding the signature of the public key of any authorised clients

And the following files on the client:

    .ssh/id_rsa – Holds the private key for the client
    .ssh/id_rsa.pub – Holds the public key for the client
    .ssh/known_hosts – Holds a list of host signatures of hosts that the client has previously connected to

A couple of caveats:

    This is for OpenSSH, commercial SSH uses different file names and formats.
    id_rsa covers keypairs generate using the RSA algorithm. If DSA is used the filename is id_dsa



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

### Tools

https://github.com/blacknbunny/CVE-2018-10933
https://github.com/koboi137/john

### Other links

https://www.ssh-audit.com/hardening_guides.html

https://www.ssh.com/ssh/keygen

https://github.com/arthepsy/ssh-audit

https://www.hackingarticles.in/6-ways-to-hack-ssh-login-password/

https://community.turgensec.com/ssh-hacking-guide

https://www.hackingarticles.in/ssh-penetration-testing-port-22/

https://community.turgensec.com/ssh-hacking-guide/

https://0xrick.github.io/hack-the-box/chainsaw/

http://pentestmonkey.net/cheat-sheet/ssh-cheat-sheet

https://www.offensive-security.com/metasploit-unleashed/scanner-ssh-auxiliary-modules/

https://sshcheck.com/
