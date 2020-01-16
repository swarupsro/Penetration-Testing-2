### Port 3389 - Remote desktop

Test logging in to see what OS is running

```
rdesktop -u guest -p guest INSERTIPADDRESS -g 94%

# Brute force
ncrack -vv --user Administrator -P /root/oscp/passwords.txt rdp://INSERTIPADDRESS
```

https://www.hackingarticles.in/penetration-testing-remote-desktop-port-3389/

https://pentestlab.blog/tag/rdp/

https://www.hackingloops.com/penetration-testing-windows-7-machine-for-remote-desktop-vulnerability/
