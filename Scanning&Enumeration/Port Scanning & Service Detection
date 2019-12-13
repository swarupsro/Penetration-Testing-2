nmap - https://nmap.org
masscan - https://github.com/robertdavidgraham/masscan
unicornscan - https://github.com/dneufeld/unicornscan

Port Scanning & Service Detection
    • unicornscan -mT -I 10.11.1.252:a -v 
    • unicornscan -mU -I 10.11.1.252:p -v 
    • nmap -sC -sV -Pn -oA  -vv standard_tcp $ip
    • nmap -sC -sV -sU -Pn -oA  -vv standard_udp $ip
    • nmap -p -sU -sT -Pn 0-65535 -vv -oN all_ports $ip 
    • unicornscan -mU -I 192.168.24.53:a -v -l unicorn_full_udp.txt ;  unicornscan -mT -I 192.168.24.53:a -v -l unicorn_full_tcp.txt
    
    nmap -sC -sV IP_ADDRESS
    nmap -sC -sV -p- IP_ADDRESS
    nmap -sU -sV --top-ports 20 IP_ADDRESS
    nmap --script vuln IP_ADDRESS
    
    Detect the service version
    $ nmap -sV -T4 -Pn -oG ServiceDetect -iL LiveHosts.txt
    $ nmap -O -T4 -Pn -oG OSDetect -iL LiveHosts.txt
    $ nmap -O -sV -T4 -Pn -p U:53,111,137,T:21-25,80,139,8080 -oG OS_Service_Detect -iL LiveHosts.txt
    
    Port found, found all the ports, but UDP port scanning will be very slow
    $ nmap -sS -T4 -Pn –top-ports 3674 -oG 3674 -iL LiveHosts.txt
    $ nmap -sS -T4 -Pn -p 0-65535 -oN FullTCP -iL LiveHosts.txt
    $ nmap -sU -T4 -Pn -p 0-65535 -oN FullUDP -iL LiveHosts.txt

