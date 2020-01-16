### Port 161/162 UDP - SNMP


```
nmap -vv -sV -sU -Pn -p 161,162 --script=snmp-netstat,snmp-processes INSERTIPADDRESS
snmp-check -t INSERTIPADDRESS -c public
```

```
# Common community strings
public
private
community
```


https://www.hackingarticles.in/6-ways-to-hack-snmp-password/


SNMP Enumeration (161):

    snmpwalk -c public -v1 10.0.0.0
    snmpcheck -t 192.168.1.X -c public
    onesixtyone -c names -i hosts
    python /usr/share/doc/python-impacket-doc/examples/samrdump.py SNMP 192.168.X.XXX
    nmap -sT -p 161 192.168.X.XXX/254 -oG snmp_results.txt
    snmpenum -t 192.168.1.X
