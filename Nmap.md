# Nmap
 - Host detection
 - Port scanning
 - Service and version detection
 - Operating system detection
 - Firewall detection
 - Detect and bypass network protection systems 
 - Vulnerability assessment
 - Bruteforce attack
 - Exloitation
### Basic Scanning Techniques

| Command   | Use   |
| ------------ | ------------ |
|nmap 192.168.10.15   |Scan a single target   |
|nmap 192.168.10.15,192.168.10.16   |Scan multiple targets   |
|nmap -iL /root/Desktop/list.txt   |Scan a list of targets   |
|nmap 192.168.10.15-30   |Scan a range of hosts   |
|nmap 192.168.10.1/24   |Scan an entire subnet   |
|nmap -iR 10   |Scan random hosts   |
|nmap 192.168.10.15-40 -exclude 192.168.10.18,192.168.10.20   |Excluding targets from a scan   |
|nmap 192.168.10.15-49 -excludefile /root/Desktop/Excludedlist.txt   |Excluding targets using a list   |
|nmap 192.168.10.15 -A   |Perform an aggressive scan   |
|nmap -6 [target]   |scan an IPv6 target   |


### Host detection (ping)
| Command   | Use   |
| ------------ | ------------ |
|nmap -sP 192.168.10.15  |a ping scan only   |
|nmap -PN 192.168.10.15   |Dont ping   |
|nmap -sn 172.16.1.1/24   |live hosts in n/w   |
|nmap -T4 -sn 192.168.10.15 -v   |ping (firewall evation)   |
|nmap -sn -PS 172.16.1.1/24   |TCP SYN ping scan(live hosts)   |
|nmap -sn -PA 172.16.1.1/24   |TCP ACK ping scan(live hosts)   |
|nmap -sn -PP 172.16.1.1/24   |ICMP Timestamp ping   |
|nmap -sn -PM 172.16.1.1/24   |ICMP address mask ping   |
|nmap -sn -PU 172.16.1.1/24   |UDP ping scan(live hosts)   |
|nmap -sn -PE 172.16.1.1/24   |ICMP ping scan(live hosts)   |
|nmap -sn -PY 172.16.1.1/24   |SCTP INIT ping scan(live hosts)   |
|nmap -sn -P0 --packet-trace 172.16.1.1/24   |IP protocol ping scan(live hosts)   |
|nmap -sn -P01,2,17 172.16.1.1/24   |Particular IP protocol ping scan (1 is ICMP 2 is IGMP 17 is UDP others TCP-6,IP-in-IP-4,SCTP-132)(live hosts)   |
|nmap -sn -PR 172.16.1.1/24   |ARP ping scan(live hosts)   |
|nmap --send-ip -sn -PS21,22,23,25,80,445,443,3389,8080 -PA80,443,8080 -P01,2,4,6 -PU631,161,137,123 172.16.1.1/24   |Advanced ping scan   |

### Reconnaissance

| Command   | Use   |
| ------------ | ------------ |
|nmap -sn --script whois-* wsj.com   |whois info   |
|nmap --tracerute --script traceroute-geolocation nmap.org   |Traceroute Geolocation   |
| nmap -sn -Pn -n --script shodan-api --script-args shodan-api.apikey=<ShodanAPI KEY> google.com  |Shodan API   |
| nmap -sn --traceroute google.com   |traceroute   |
|nmap -R 192.168.10.15   |Force reverse DNS resolution   |
|nmap -n 192.168.10.15   |Disable reverse DNS resolution   |
|nmap -system-dns [servers] 192.168.10.15   |Alternative DNS lookup   |
|nmap -sL 192.168.10.15   |Create a host list   |


### Extarcting Informations from Windows Systems

| Command   | Use   |
| ------------ | ------------ |
|nmap -sU -p137 --script nbstat 192.168.10.15   |NetBIOS name and MAC address   |
|nmap -p139,445 --script smb-os-discovery 192.168.10.15   |SMB discovery   |
|nmap -p137,139,445 --script smb-security-mode 192.168.10.15   |SMB signing   |
| nmap -p139,445 --script smb-enum-users 192.168.10.15   |User accounts Enumeration   |
|nmap -p445 --script smb-enum-sessions 192.168.10.15   |Enumerating SMB sessions   |
|nmap -p139,445 --script smb-enum-shares 192.168.10.15   |Enumerating shares   |
|nmap -p445 --script smb-enum-shares --script-args=smbuser=root,smbpass=123 192.168.10.15   |Enumerating shares   |
|nmap -p445 --script smb-enum-shares --script-args=smbuser=root,smbhash=cdoieneeuern3hrje832j 192.168.10.15   |Enumerating shares   |
|nmap -p445 --script smb-enum-processes --script-args=smbuser=root,smbpass=123 192.168.10.15   |Enumerating proccess   |
|nmap -p445 --script smb-system-info  192.168.10.15   |system info   |
|nmap -p445 --script smb-brute  192.168.10.15   |valid usernames and passwords   |
|nmap -p389 -sV 192.168.10.15   |Domain controllers   |


### Port scanning

| Command   | Use   |
| ------------ | ------------ |
|nmap 192.168.10.15   |listing open ports   |
|nmap 192.168.10.15 -p80,443   |scan particular ports   |
|nmap 192.168.10.15 -p1-100   |scan range of ports   |
|nmap 192.168.10.15 -p-   |scan all ports   |
|nmap -e eth0 192.168.10.15   |scan specific interface   |


### Firewall Evasion Techniques

| Command   | Use   |
| ------------ | ------------ |
|nmap -f 192.168.10.15   |Fragment packets   |
|nmap -mtu [MTU] 192.168.10.15   |Specify specific MTU   |
|nmap -D RND: [number] 192.168.10.15   |Use a decoy   |
|nmap -sI [zombie] 192.168.10.15   |Idle zombie scan   |
|nmap -source-port [port] 192.168.10.15   |Manually specify a source port   |
|nmap -data-length [size] 192.168.10.15   |Append random data   |
|nmap -randomize-hosts [size] 192.168.10.15   |Randamize target scan order  |
|nmap -sppof-mac [mac|0|vendor] 192.168.10.15   |Spoof MAC Address   |
|nmap -badsum 192.168.10.15   |Send bad checksums   |


### Version Detection

| Command   | Use   |
| ------------ | ------------ |
|nmap -O 192.168.10.15   |OS detection   |
|nmap -O -osscan-guess 192.168.10.15   |Attempt to guess an unknown   |
|nmap -sv 192.168.10.15   |service version   |
|nmap -sv -version-trace 192.168.10.15   |Troubleshooting version scans   |
|nmap -sR 192.168.10.15   |Perfrom a RPC scan   |


### Output file

| Command   | Use   |
| ------------ | ------------ |
|nmap -oN result.txt 192.168.10.15   |save output to text file   |
|nmap -T4 -F -oX results.xml 192.168.10.15   |save output to xml file   |
|nmap -oG result.txt 192.168.10.15   |Grepable output   |
|xsltproc results.xml -o results.htlm   |convert xml to html   |














nmap -T4 -v -PN -n -sS --top-ports 100 --max-parallelism 10 -oA nmapSYN 192.168.10.10
nmap -T5 -PN -v -A -oA nmapComplete 192.168.10.10
