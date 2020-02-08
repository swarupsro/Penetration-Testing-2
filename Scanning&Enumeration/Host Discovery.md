
* nmap -sP 10.0.0.0/24 
* nmap -sn 10.0.0.0/24
* nmap -sn  10.11.1.1-254 -vv -oA hosts
* nmap -sS -T4 -Pn -oG TopTCP -iL LiveHosts.txt
* nmap -sU -T4 -Pn -oN TopUDP -iL LiveHosts.txt
* nmap -sn -T4 -oG Discovery.gnmap 192.168.1.1/24
* nmap 10.0.0.0/24
* nmap -F 10.0.0.0/24
* nmap -p 22 10.0.0.0/24
* nmap -p 22-53 10.0.0.0/24
* nmap -T1 10.0.0.1

Customise ICMP
------------------
* nmap -sP -PP 10.0.0.0/24

Customise TCP Ping
-----------------------
* nmap -sP -PS 10.0.0.0/24
* nmap -sP -PS 10.0.0.0/24 -g22

TCP Ping +ARP
-----------------
* nmap -PA google.com
* nmap -PR 10.0.0.0/24

ARP Table
-----------
* nmap -PR nmap -PR 10.0.0.0/24

max RTT Timeout
-------------------
* nmap --max-rtt-timeout 250ms --initial-rtt-timeout 150ms google.com
   
   
   
   
   * netdiscover -r 10.11.1.0/24
   * python3 autorecon.py $ip -v
   * grep “Status: Up” Discovery.gnmap | cut -f 2 -d ‘ ‘ > LiveHosts.txt
   * masscan
