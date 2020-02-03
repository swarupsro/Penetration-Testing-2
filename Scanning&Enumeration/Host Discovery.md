   * nmap -sn  10.11.1.1-254 -vv -oA hosts
   • netdiscover -r 10.11.1.0/24
   • python3 autorecon.py $ip -v
   • masscan
   
   Host discovery, generate a list of surviving hosts
   $ nmap -sn -T4 -oG Discovery.gnmap 192.168.1.1/24
   $ grep “Status: Up” Discovery.gnmap | cut -f 2 -d ‘ ‘ > LiveHosts.txt
   
   $ nmap -sS -T4 -Pn -oG TopTCP -iL LiveHosts.txt
   $ nmap -sU -T4 -Pn -oN TopUDP -iL LiveHosts.txt
