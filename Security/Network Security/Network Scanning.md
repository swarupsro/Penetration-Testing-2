# Introduction to Network Vulnerability Scanning
-------------------------------------------------
 ### 1.Basic networks and their components 
A basic corporate network typically consists of endpoints such as desktops/laptops, servers, security devices such as Firewall,
proxy, intrusion detection and prevention systems, and network devices such as hubs, switches, and routers.
These components can be attacked by a hacker using publicly available exploits or a zero-day vulnerability to gain access 
to the device/machine with a possibility of gaining access to a different device/machine in the network or whole network itself

 ### 2.Network Vulnerability Scanning (Internal and External)
A vulnerability is a weakness present in a system or device that is exposed to a possibility of being attacked. 
Network Vulnerability Scanning is a process of looking into identifying and detecting vulnerabilities in the network 
components such as clients, servers, network devices, and endpoints, using various automated or manual tools and techniques. 
It can be broadly classified into two types: internal network vulnerability scan and external network vulnerability scan. 
An external vulnerability scan has a scope to identify loopholes with a perspective of the attacker being over the internet 
and targeting the network through public IP addresses of the network, whereas an internal vulnerability scan operates 
considering the attacker to be an insider with access to the internal network and targeting the network through 
private IP addresses.In general, there are two types of scanning techniques that can be used, authenticated and unauthenticated.
The activity of a Network Vulnerability Scan can be divided into three phases: 
 
 - Discovery 
 - Port scanning 
 - Vulnerability scanning

## Discovery 
Discovery, also known as , is a process to enumerate live hosts and is a very Host Discovery important component 
of the reconnaissance phase of a security testing activity. 
This will help you to eliminate the unwanted hosts from the list of targets, 
thus it will allow you to use these enumerated hosts to perform targeted scans and penetration tests.  
Some of the tools that can be used to perform Network Discovery are Nmap, Nessus, OpenVas, and Wireshark. 
eg:-\\nmap -Pn 192.168.10.34 (ping scan)

## Port scanning 
In this phase, we will perform detection of the ports open for a specific host based on the communication 
between the host on that port to your machine. This technique helps to determine whether a particular 
port is open or closed. This technique differs from protocol to protocol. For example, for TCP, 
the communication and the pattern to conclude a port to be open is different when compared to UDP. 
Some of the tools that can be used to perform port scanning are Nmap, Nessus, OpenVas, and Wireshark. 
eg:-\\nmap -sS -p80 192.168.10.34

## Vulnerability scanning 
Once the open ports are identified on the discovered live hosts, we can perform vulnerability scanning. 
A vulnerability scan detects and identifies known issues of the software and tools installed on a host 
such as older version of software in use, vulnerable protocols enabled, and default passwords. 
It is difficult to perform this activity manually; hence this phase needs to be performed using automated tools 
that identify the open ports and try various exploits on the ports to identify whether the particular 
process/software using the port is vulnerable to the exploit based on the process.
Some of the tools used to perform vulnerability scanning are Nessus, OpenVas, and Qualys. 

Network Vulnerability Scan provides a bundle of information useful to both administrators and penetration testers, 
such as the following: 

- Unwanted ports are open and services running 
- Default user account and password information 
- Missing patches, updates, and upgrades 
- Vulnerable version of software installed 
- Vulnerable protocols in use 
- Vulnerable algorithms in use 
- Exploit information for all the preceding vulnerabilities

Along with the previous technical use cases, a network vulnerability also has various uses from an 
organization's perspective, such as the following: 

- Giving importance and bringing focus to information security 
- Helping to find potential risks proactively 
- Resulting in network update 
- Advancing development in the administrative knowledge 
- Preventing financial loss in critical infrastructures 
- Prioritizing the vulnerabilities that require escalated patching versus delayed patching

## Complexity
Today's network environments have a complex structure consisting of firewalls, DMZ, and network devices such as switches and routers. 
These devices consist of complex access lists and virtual network configurations, which makes it difficult to generalize any activity. 
A shift in any of the preceding configurations could result in a change of the architecture of the whole network.

If we are looking to perform an IP-based scan on any of the network components, we have to be sure that all the 
data packets generated are reaching the destination intact and are not being impacted by any of the devices or solutions in between 

In order to perform a successful security profiling using a Network Vulnerability Scan, the following factors need to be considered: 

- Scope of the scan 
- Network architecture 
- Network access

Flow of procedures used in Network Vulnerability Scanning 
Uses of performing a Network Vulnerability Scan 
Complexity of performing network scans 
How to devise a mitigation plan and respond



## Scope of the scan 
If we are required to perform a vulnerability assessment for a specific application's infrastructure, it is very important to identify the data transmission sources and the components involved in the end-to-end communication. This will allow the penetration tester to perform the vulnerability scan on this scope and identify vulnerabilities specific to this application. Instead, if we choose to scan the subnets or a broader range of IP addresses, we might end up highlighting unnecessary vulnerabilities, which most of the time leads to confusion during the remediation phase. For example, if we are looking to audit a web-based application, we might be looking to include a web application, application server, web server, and database server as part of the audit scope.

## Network architecture 
It is always important to understand the placement of the IP address or the component on which we are performing vulnerability scanning. This will help us to customize our approach and to reduce false positives. For example, if Alice is trying to scan a web application hosted behind a web application firewall, she needs to customize the payloads or the scripts used to identify vulnerabilities using techniques such as encoding, to ensure that the payloads are not blocked by the web application firewall.

## Network access 
When tasked to perform Network Vulnerability Scans on a huge network, it is very important to know whether proper access has been provided to your appliance or host to perform the scanning activity. A network vulnerability scan performed without proper network access will yield incomplete results. It is always recommended to have the scanner appliance or host IP address to be whitelisted across the network devices to obtain full access to the scope of the scan.


## Response 
Once a Network Vulnerability Scan report is obtained, it is important to devise a mitigation plan to mitigate all the vulnerabilities highlighted as part of the report. The following are a few solutions that can be part of the Network Security Scan report: 

 - Close unwanted ports and disable unwanted services 
 - Use strong and uncommon passwords 
 - Always apply latest patches and updates 
 - Uninstall or update older versions of software 
 - Disable legacy and old protocols in use 
 - Use strong algorithms and authentication mechanism 
