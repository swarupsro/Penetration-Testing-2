# Ports

|**Port Number**|**Protocol**|**Service & Application (Enumeration&Exploits)**|
|:--------------|:-----------|:------------------------|
|1|tcp|blackice||
|7|tcp|echo|
|11|tcp|systat|
|13|tcp|daytime|
|15|tcp|netstat|
|17|tcp|quote of the day|
|19|tcp|character generator|
|21|tcp|[FTP](https://github.com/sarathlalup/Penetration-Testing/blob/master/Penetration%20Testing/FTP%20Server%20(Port%2021).md)|
|22|tcp|ssh|
|23|tcp|telnet|
|25|tcp|smtp|
|26|tcp|ssh|
|37|tcp|rdate|
|49|tcp|TACACS+|
|53|tcp|[DNS](https://github.com/sarathlalup/Penetration-Testing/blob/master/Penetration%20Testing/DNS%20(Port%2053).md)|
|53|udp|dns|
|67|tcp|[DHCP](https://github.com/sarathlalup/Penetration-Testing/blob/master/Penetration%20Testing/DHCP%20Server%20(Port%2067).md)|
|68|tcp|dhclient|
|69|udp|TFTP,BitTorrent|
|70|tcp|Gopher|
|79|tcp|[Finger](https://github.com/sarathlalup/Penetration-Testing/blob/master/Penetration%20Testing/Finger%20(Port%2079).md)|
|80|tcp|[HTTP,malware](https://github.com/sarathlalup/Penetration-Testing/blob/master/Penetration%20Testing/HTTP&HTTPS%20(Port%2080,443).md)|
|81|tcp|HTTP,malware|
|82|tcp|HTTP,malware|
|83|tcp|HTTP|
|84|tcp|HTTP|
|88|tcp|Kerberos|
|102|tcp|Siemens S7|
|110|tcp|pop3|
|111|tcp|RPC|
|119|tcp|NNTP||
|123|tcp|NTP||
|123|udp|ntp|
|137|tcp|NetBIOS|nbtscan -A `target`|
|143|tcp|IMAP|
|161|udp|snmp|
|175|tcp|IBM Network Job Entry|
|179|tcp|BGP|
|195|tcp|TA14-353a|
|311|tcp|OS X Server Manager|
|389|tcp|[LDAP](https://github.com/sarathlalup/Penetration-Testing/blob/master/Penetration%20Testing/LDAP%20(Port%20389).md)|
|443|tcp|https|
|445|tcp|
|465|tcp|smtps|
|500|udp|ike|
|502|tcp|modbus|
|503|tcp|modbus|
|512|tcp||
|513|tcp||
|514|tcp||
|515|tcp|Line Printer Daemon|
|520|tcp|RIP|
|523|tcp|IBM DB2|
|554|tcp|RTSP|
|587|tcp|SMTP mail submission|
|623|tcp|IPMI|
|626|tcp|OS X serialnumbered|
|631|tcp|CUPS Service error|
|636|tcp|ldaps|
|771|tcp|Realport|
|789|tcp|Redlion Crimson3||
|873|tcp|rsync|
|902|tcp|VMware authentication|
|992|tcp|Telnet(secure)|
|993|tcp|[IMAPs](https://github.com/sarathlalup/Penetration-Testing/blob/master/Penetration%20Testing/IMAPS%20(Port%20993).md)|
|995|tcp|POP3s|
|1023|tcp|telnet|
|1025|tcp|Kamstrup|
|1099|tcp||
|1194|tcp|openvpn|
|1200|tcp|Codesys|
|1234|udp|udpxy|
|1202|tcp|linknat|
|1433|udp|[MS-SQL](https://github.com/sarathlalup/Penetration-Testing/blob/master/Penetration%20Testing/MS-SQL%20(Port%201433).md)|
|1494||[Citrix](https://github.com/sarathlalup/Penetration-Testing/blob/master/Penetration%20Testing/Citrix%20(Port%201494).md)|
|1604||Citrix, malware|
|1723|tcp|pptp|
|1741||CiscoWorks|
|1833||MQTT|
|1900|tcp|bes,UPnP|
|1911||Niagara Fox|
|1962||PCworx|
|2000||iKettle,MikroTik bandwidth test|
|2049|tcp|nfs|
|2121|tcp|ftp|
|2082|tcp|cpanel|
|2083|tcp|cpanel|
|2086||WHM|
|2087||WHM|
|2123||GTPv1|
|2152||GTPv1||
|2182||Apache Zookeeper||
|2222|tcp|SSH, PLC5, EtherNet/IP||
|2323|tcp|telnet||
|2332|tcp|Sierra wireless(telnet)||
|2375||Docker||
|2376||Docker||
|2404||IEC-104||
|2455||CoDeSys||
|2480||OrientDB||
|2628||Dictionary||
|3000||ntop||
|3128|tcp|squid||
|3299|tcp|sap|
|3310|tcp|ClamAV||
|3386||GTPv1||
|3388||RDP||
|3389||RDP||
|3541||PBX GUI||
|3542||PBX GUI||
|3632|tcp|distccd|
|3689||DACP||
|3780||Metasploit||
|3787||Ventrilo||
|4022||udpxy||
|4369|tcp|Erlang Port Mapper Daemon|
|4440|tcp|rundeck||
|4500||IKE NAT-T(VPN)||
|4567||Modem web interface||
|4070||VertX/Edge door controller||
|4800||Noxa Nport||
|4911||Niagara Fox with SSL||
|4949||Munin||
|5006||MELSEC-Q||
|5007||MELSEC-Q||
|5008||NetMobility||
|5009||Apple Aitport Administrator||
|5038|tcp|Asterisk Call Manager|
|5432|tcp|postgresql||
|5060|udp|sip|msf > use auxiliary/scanner/sip/options|
|5222||XMPP||
|5269||XMPP Server to Server||
|5353||mDNS||
|5357||Mirosoft-HTTP API/2.0||
|5432||Postgresql||
|5555|tcp|hp data protector|
|5577||Flux LED||
|5601|tcp|kibana||
|5632||PCAnywhere||
|5672||RabbitMQ||
|5900|tcp|vnc|msf > 
|5901||vnc||
|5938||TeamViewer||
|5984||CouchDB||
|5985|tcp|winrm|
|6000|tcp|x11|
|6379|tcp|redis|
|6380|tcp|redis||
|6082|tcp|varnish||
|6667|tcp|ircd backdoor|
|6881||BitTorrent||
|6969||TFTP,BitTorrent||
|7001|tcp|weblogic||
|8080|tcp|jekins|
|8083|tcp|vestacp||
|8089|tcp|jboss||
|8101|tcp|apache karaf||
|8180|tcp|apache tomcat|
|8443|tcp|https||
|8554|tcp|rtsp||
|8649|tcp|ganglia||
|9009|tcp|Julia||
|9151|tcp|Tor Control||
|9160||Apache Cassandra||
|9200|tcp|elasticsearch|
|9418|tcp|git||
|10000|tcp|virtualmin/webmin||
|11211|tcp|memcache|
|13579||Media Player classic web interface||
|15672|tcp|rabbitmq|
|17185||VxWorks WDBRPC||
|18083|tcp|vbox server||
|27017|tcp|mongodb|
|28017|tcp|mongodb||
|37777||Dahua DVR||
|44818||EtherNet/IP||
|49153||WeMo Link||
|50000|tcp|sap||
|50030|tcp|hadoop||
|50070|tcp|hadoop||
|51106||Deluge(HTTP)||
|54138||Toshiba PoS||
|55553||Metasploit|
|55554||Metasploit|
|62078||Apple iDevice|
|64738||Mumble|

# Links

1. http://www.rfc-editor.org/search/rfc_search.php
2. http://packetlife.net/
3. https://www.leanpub.com/shodan
