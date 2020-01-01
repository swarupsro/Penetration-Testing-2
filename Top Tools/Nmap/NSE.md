NMAP Scripting Engine (NSE)

•	Vulnerability detection
•	Backdoor detection
•	Vulnerability exploitation
•	NSE is activated with the -sC option (or –script if you wish to specify a custom set of scripts)


### Nmap Scripting Engine 
|Command   |Use   |
| ------------ | ------------ |
|nmap –script [script.nse] 192.168.10.15   |Execute individual scripts   |
|nmap –script [expression] 192.168.10.15   |Execute multiple scripts   |
|nmap –script [cat] 192.168.10.15 |Execute scripts by category   |
|nmap –script [cat1,cat2, etc] 192.168.10.15   |Execute multiple scripts categories   |
|nmap –script [script] –script-trace 192.168.10.15   |Troubleshoot scripts   |
|nmap –script-updatedb    |Update the script database   |
|   |   |

|Script categories   |Use   |
| ------------ | ------------ |
|all   | 
|auth   |Utilize credentials or bypass authentication on target hosts  |
|default   |Scripts run automatically when -sC or -A are used   |
|broadcas   | Discover hosts not included on command line by broadcasting on local network   |
|brute   | Attempt to guess passwords on target systems, for a variety of protocols, including http, SNMP, IAX, MySQL, VNC, etc   |
|dos   | May cause denial of service conditions in target hosts   |
|exploit   | Attempt to exploit target systems   |
|discovery   |Try to learn more information about target hosts through public sources of information, SNMP, directory services, and more   |
|external   |Interact with third-party systems not included in target list    |
|intrusive   |May crash target, consume excessive resources, or otherwise impact target machines in a malicious fashion   |
|malware   | Look for signs of malware infection on the target hosts    |
|safe   |Designed not to impact target in a negative fashion   |
|vuln   | Measure whether target systems have a known vulnerability   |
|version   |Measure the version of software or protocol spoken by target hosts   |
|fuzzer   |Send unexpected input in network protocol fields   |

