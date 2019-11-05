# Security Tool Chest

Anticipating and mitigating security threats is critical during software development. This paper is going to detail and investigate security vulnerabilities and mitigation strategies to help software developers build secure applications and prevent operating system leaks. This paper examines common vulnerabilities, and provides relevant mitigation strategies, from several relevant perspectives. This paper hopes to encompasses the cyber Kill chain as part of the five stage compramision stages, displaying relevant tools, books and strategies at each stage.
___________________________________________________________________________________________________________

<img src="https://camo.githubusercontent.com/7ed924f85b775db73958b443a8798b401c40cdd2/68747470733a2f2f75706c6f6164732d73736c2e776562666c6f772e636f6d2f3538383636636165616263383364356537633537346337312f3538626534333132646331336239646537343638363132615f5265642d5465616d2d41747461636b2d4c6966656379636c652e6a7067" width="600">

## Contents
* [Reconnaissance](#reconnaissance)
* [Weaponization](#weaponization)
* [Delivery](#delivery)
* [Command and Control](#command-and-control)
* [Lateral Movement](#lateral-movement)
* [Establish Foothold](#establish-foothold)
* [Escalate Privileges](#escalate-privileges)
* [Data Exfiltration](#data-exfiltration)
* [DLL Architecture](#DLL-Architecture)
* [References](#references)

## Reconnaissance
### Active Intelligence Gathering
Under this method, the targeted organization may become aware of the ongoing reconnaissance process since the pentester is actively engaging with the target. During this phase, he takes an active part in mapping network infrastructure, then he enumerates and/or scans the open services for vulnerabilities, and eventually searches for unpublished directories, files and servers. Other similar activities include OS Fingerprinting, Banner grabbing, and Web server application scan.
* **Nmap** is used to discover hosts and services on a computer network, thus building a "map" of the network. https://github.com/nmap/nmap
* **dnsrecon** a tool DNS Enumeration Script. https://github.com/darkoperator/dnsrecon
* **EyeWitness** is designed to take screenshots of websites, provide some server header info, and identify default credentials if possible. https://github.com/ChrisTruncer/EyeWitness
* **AWSBucketDump** is a tool to quickly enumerate AWS S3 buckets to look for loot. https://github.com/jordanpotti/AWSBucketDump
* **AQUATONE** is a set of tools for performing reconnaissance on domain names. https://github.com/michenriksen/aquatone
* **spoofcheck** a program that checks if a domain can be spoofed from. The program checks SPF and DMARC records for weak configurations that allow spoofing. https://github.com/BishopFox/spoofcheck

### Passive Intelligence Gathering
This option is under discussion provided that there is an explicit demand for the gathering activities not to be detected by the target. In this regard, the pentester cannot use tools that send traffic to the targeted company neither from his host nor an “anonymous” one across the Internet. Not only will that be technically burdening but also the person who performs the pentest will have to substantiate his findings with whatever he can dig out from archived or stored information, which is at times not up to date and incorrect because it has been limited to inquiries collected from third parties.
* **linkScrape** A LinkedIn user/company enumeration tool. https://github.com/NickSanzotta/linkScrape
* **FOCA** (Fingerprinting Organizations with Collected Archives) is a tool used mainly to find metadata and hidden information in the documents its scans. https://github.com/ElevenPaths/FOCA
* **theHarvester** is a tool for gathering subdomain names, e-mail addresses, virtual
hosts, open ports/ banners, and employee names from different public sources. https://github.com/laramies/theHarvester
* **Metagoofil** is a tool for extracting metadata of public documents (pdf,doc,xls,ppt,etc) availables in the target websites. https://github.com/laramies/metagoofil
* **Social Mapper** OSINT Social Media Mapping Tool, takes a list of names & images (or LinkedIn company name) and performs automated target searching on a huge scale across multiple social media sites. Not restricted by APIs as it instruments a browser using Selenium. Outputs reports to aid in correlating targets across sites. https://github.com/SpiderLabs/social_mapper
* **skiptracer** OSINT scraping framework, utilizes some basic python webscraping (BeautifulSoup) of PII paywall sites to compile passive information on a target on a ramen noodle budget. https://github.com/xillwillx/skiptracer
* **typofinder** a finder of domain typos showing country of IP address. https://github.com/nccgroup/typofinder
* **pwnedOrNot** is a python script which checks if the email account has been compromised in a data breach, if the email account is compromised it proceeds to find passwords for the compromised account. https://github.com/thewhiteh4t/pwnedOrNot

### Frameworks
In computer programming, a software framework is an abstraction in which software providing generic functionality can be selectively changed by additional user-written code, thus providing application-specific software. A software framework provides a standard way to build and deploy applications.
* **Maltego** is a unique platform developed to deliver a clear threat picture to the environment that an organization owns and operates. https://www.paterva.com/web7/downloads.php
* **SpiderFoot** the open source footprinting and intelligence-gathering tool. https://github.com/smicallef/spiderfoot
* **datasploit** is an OSINT Framework to perform various recon techniques on Companies, People, Phone Number, Bitcoin Addresses, etc., aggregate all the raw data, and give data in multiple formats. https://github.com/DataSploit/datasploit
* **Recon-ng** is a full-featured Web Reconnaissance framework written in Python. https://bitbucket.org/LaNMaSteR53/recon-ng

## Social Engineering in the Context of Intelligence Gathering
Social engineering is deemed one of the most widespread avenues for gathering information on a particular individual or a firm. A lot of information is out there – just check the popular social media websites. Also, websites like Pipl, PeekYou, and Spokeo may come in handy as they will provide access to email addresses, locations, phone numbers, and even family tree information.

* **Eavesdropping** 
* **Shoulder Surfing** 

## Honeypot
A Honeypot is a computer security mechanism set to detect, deflect, or, in some manner, counteract attempts at unauthorized use of information systems. Generally, a honeypot consists of data (for example, in a network site) that appears to be a legitimate part of the site, but is actually isolated and monitored, and that seems to contain information or a resource of value to attackers, who are then blocked.
* **awesome-honeypots** The canonical awesome honeypot list. https://github.com/paralax/awesome-honeypots
* **HoneyPy** HoneyPy is a low to medium interaction honeypot. It is intended to be easy to: deploy, extend functionality with plugins, and apply custom configurations. https://github.com/foospidy/HoneyPy
* **Dionaea** Dionaea is meant to be a nepenthes successor, embedding python as scripting language, using libemu to detect shellcodes, supporting ipv6 and tls. https://github.com/DinoTools/dionaea
* **Conpot** ICS/SCADA Honeypot. Conpot is a low interactive server side Industrial Control Systems honeypot designed to be easy to deploy, modify and extend. By providing a range of common industrial control protocols we created the basics to build your own system, capable to emulate complex infrastructures to convince an adversary that he just found a huge industrial complex. To improve the deceptive capabilities, we also provided the possibility to server a custom human machine interface to increase the honeypots attack surface. The response times of the services can be artificially delayed to mimic the behaviour of a system under constant load. Because we are providing complete stacks of the protocols, Conpot can be accessed with productive HMI's or extended with real hardware. Conpot is developed under the umbrella of the Honeynet Project and on the shoulders of a couple of very big giants. https://github.com/mushorg/conpot
* **Amun** Amun Python-based low-interaction Honeypot. https://github.com/zeroq/amun
* **Glastopf** Glastopf is a Honeypot which emulates thousands of vulnerabilities to gather data from attacks targeting web applications. The principle behind it is very simple: Reply the correct response to the attacker exploiting the web application. https://github.com/mushorg/glastopf
* **Kippo** Kippo is a medium interaction SSH honeypot designed to log brute force attacks and, most importantly, the entire shell interaction performed by the attacker. https://github.com/desaster/kippo
* **Kojoney** Kojoney is a low level interaction honeypot that emulates an SSH server. The daemon is written in Python using the Twisted Conch libraries. https://github.com/hydrogen18/kojoney/blob/master/kojoney.py
* **HonSSH** HonSSH is a high-interaction Honey Pot solution. HonSSH will sit between an attacker and a honey pot, creating two separate SSH connections between them. https://github.com/tnich/honssh
* **Bifrozt** Bifrozt is a NAT device with a DHCP server that is usually deployed with one NIC connected directly to the Internet and one NIC connected to the internal network. What differentiates Bifrozt from other standard NAT devices is its ability to work as a transparent SSHv2 proxy between an attacker and your honeypot. If you deployed an SSH server on Bifrozt’s internal network it would log all the interaction to a TTY file in plain text that could be viewed later and capture a copy of any files that were downloaded. You would not have to install any additional software, compile any kernel modules or use a specific version or type of operating system on the internal SSH server for this to work. It will limit outbound traffic to a set number of ports and will start to drop outbound packets on these ports when certain limits are exceeded. https://github.com/Bifrozt
* **Cuckoo Sandbox** Cuckoo Sandbox is an Open Source software for automating analysis of suspicious files. To do so it makes use of custom components that monitor the behavior of the malicious processes while running in an isolated environment. https://cuckoosandbox.org/
## Weaponization
The cyber attacker does not interact with the intended victim. Instead, they create their attack. For example, the attacker may create an infected Microsoft Office document paired with a customized phishing email, or perhaps they create a new strain of self-replicating malware to be distributed via USB drive. There are few security controls, including security awareness, that may impact or neutralize this stage, unless the cyber attacker does some limited testing on the intended target.
* **demiguise** is a HTA encryption tool for RedTeams. https://github.com/nccgroup/demiguise
* **Office-DDE-Payloads** collection of scripts and templates to generate Office documents embedded with the DDE, macro-less command execution technique. https://github.com/0xdeadbeefJERKY/Office-DDE-Payloads
* **CACTUSTORCH** Payload Generation for Adversary Simulations. https://github.com/mdsecactivebreach/CACTUSTORCH
* **SharpShooter** is a payload creation framework for the retrieval and execution of arbitrary CSharp source code. https://github.com/mdsecactivebreach/SharpShooter
* **Don't kill my cat** is a tool that generates obfuscated shellcode that is stored inside of polyglot images. The image is 100% valid and also 100% valid shellcode. https://github.com/Mr-Un1k0d3r/DKMC
* **Malicious Macro Generator Utility** Simple utility design to generate obfuscated macro that also include a AV / Sandboxes escape mechanism. https://github.com/Mr-Un1k0d3r/MaliciousMacroGenerator
* **Invoke-DOSfuscation** cmd.exe Command Obfuscation Generator & Detection Test Harness. https://github.com/danielbohannon/Invoke-DOSfuscation
* **morphHTA** Morphing Cobalt Strike's evil.HTA. https://github.com/vysec/morphHTA
* **Unicorn** is a simple tool for using a PowerShell downgrade attack and inject shellcode straight into memory. https://github.com/trustedsec/unicorn
* **Shellter** is a dynamic shellcode injection tool, and the first truly dynamic PE infector ever created. https://www.shellterproject.com/
* **EmbedInHTML** Embed and hide any file in an HTML file. https://github.com/Arno0x/EmbedInHTML
* **SigThief** Stealing Signatures and Making One Invalid Signature at a Time. https://github.com/secretsquirrel/SigThief
* **LuckyStrike** a PowerShell based utility for the creation of malicious Office macro documents. To be used for pentesting or educational purposes only. https://github.com/curi0usJack/luckystrike
* **ClickOnceGenerator** Quick Malicious ClickOnceGenerator for Red Team. The default application a simple WebBrowser widget that point to a website of your choice. https://github.com/Mr-Un1k0d3r/ClickOnceGenerator
* **macro_pack** is a tool by @EmericNasi used to automatize obfuscation and generation of MS Office documents, VB scripts, and other formats for pentest, demo, and social engineering assessments. https://github.com/sevagas/macro_pack
* **StarFighters** a JavaScript and VBScript Based Empire Launcher. https://github.com/Cn33liz/StarFighters
* **nps_payload** this script will generate payloads for basic intrusion detection avoidance. It utilizes publicly demonstrated techniques from several different sources. https://github.com/trustedsec/nps_payload
* **SocialEngineeringPayloads** a collection of social engineering tricks and payloads being used for credential theft and spear phishing attacks. https://github.com/bhdresh/SocialEngineeringPayloads
* **The Social-Engineer Toolkit** is an open-source penetration testing framework designed for social engineering. https://github.com/trustedsec/social-engineer-toolkit
* **Phishery** is a Simple SSL Enabled HTTP server with the primary purpose of phishing credentials via Basic Authentication.  https://github.com/ryhanson/phishery
* **PowerShdll** run PowerShell with rundll32. Bypass software restrictions. https://github.com/p3nt4/PowerShdll
* **Ultimate AppLocker ByPass List** The goal of this repository is to document the most common techniques to bypass AppLocker. https://github.com/api0cradle/UltimateAppLockerByPassList
* **ps1encode** use to generate and encode a powershell based metasploit payloads. https://github.com/CroweCybersecurity/ps1encode
* **Worse PDF** turn a normal PDF file into malicious. Use to steal Net-NTLM Hashes from windows machines. https://github.com/3gstudent/Worse-PDF


## Delivery
Transmission of the attack to the intended victim(s). For example, this would be sending the actual phishing email or distributing the infected USB drives at a local coffee shop or cafe. While there is an entire technical industry dedicated to stopping this stage, people also play a critical role.
### Phishing
Phishing is the fraudulent attempt to obtain sensitive information such as usernames, passwords and credit card details by disguising oneself as a trustworthy entity in an electronic communication.
* **PwnAuth** a web application framework for launching and managing OAuth abuse campaigns. https://github.com/fireeye/PwnAuth
* **Phishing Frenzy** Ruby on Rails Phishing Framework. https://github.com/pentestgeek/phishing-frenzy
* **King Phisher** is a tool for testing and promoting user awareness by simulating real world phishing attacks. https://github.com/securestate/king-phisher
* **FiercePhish** is a full-fledged phishing framework to manage all phishing engagements. It allows you to track separate phishing campaigns, schedule sending of emails, and much more. https://github.com/Raikia/FiercePhish
* **ReelPhish** is a Real-Time Two-Factor Phishing Tool. https://github.com/fireeye/ReelPhish/
* **Gophish** is an open-source phishing toolkit designed for businesses and penetration testers. It provides the ability to quickly and easily setup and execute phishing engagements and security awareness training. https://github.com/gophish/gophish
* **CredSniper** is a phishing framework written with the Python micro-framework Flask and Jinja2 templating which supports capturing 2FA tokens. https://github.com/ustayready/CredSniper
* **BeEF** is short for The Browser Exploitation Framework. It is a penetration testing tool that focuses on the web browser. https://github.com/beefproject/beef

## Command and Control
### Remote Access Tools
In computing, the term remote desktop refers to a software or operating system feature that allows a personal computer's desktop environment to be run remotely on one system, while being displayed on a separate client device. Remote desktop applications have varying features.
* **Cobalt Strike** is software for Adversary Simulations and Red Team Operations. https://cobaltstrike.com/
* **Empire** is a post-exploitation framework that includes a pure-PowerShell2.0 Windows agent, and a pure Python 2.6/2.7 Linux/OS X agent. https://github.com/EmpireProject/Empire
* **Metasploit Framework** is a computer security project that provides information about security vulnerabilities and aids in penetration testing and IDS signature development. https://github.com/rapid7/metasploit-framework
* **SILENTTRINITY** A post-exploitation agent powered by Python, IronPython, C#/.NET. https://github.com/byt3bl33d3r/SILENTTRINITY
* **Pupy** is an opensource, cross-platform (Windows, Linux, OSX, Android) remote administration and post-exploitation tool mainly written in python. https://github.com/n1nj4sec/pupy
* **Koadic** or COM Command & Control, is a Windows post-exploitation rootkit similar to other penetration testing tools such as Meterpreter and Powershell Empire. https://github.com/zerosum0x0/koadic
* **PoshC2** is a proxy aware C2 framework written completely in PowerShell to aid penetration testers with red teaming, post-exploitation and lateral movement. https://github.com/nettitude/PoshC2_Python
* **Gcat** a stealthy Python based backdoor that uses Gmail as a command and control server. https://github.com/byt3bl33d3r/gcat
* **TrevorC2** is a legitimate website (browsable) that tunnels client/server communications for covert command execution. https://github.com/trustedsec/trevorc2
* **Merlin** is a cross-platform post-exploitation HTTP/2 Command & Control server and agent written in golang. https://github.com/Ne0nd0g/merlin
* **Quasar** is a fast and light-weight remote administration tool coded in C#. Providing high stability and an easy-to-use user interface, Quasar is the perfect remote administration solution for you. https://github.com/quasar/QuasarRAT
* **Covenant** is a .NET command and control framework that aims to highlight the attack surface of .NET, make the use of offensive .NET tradecraft easier, and serve as a collaborative command and control platform for red teamers. https://github.com/cobbr/Covenant
* **FactionC2** is a C2 framework which use websockets based API that allows for interacting with agents and transports. https://github.com/FactionC2/
* **DNScat2** is a tool is designed to create an encrypted command-and-control (C&C) channel over the DNS protocol. https://github.com/iagox86/dnscat2
* **Sliver** is a general purpose cross-platform implant framework that supports C2 over Mutual-TLS, HTTP(S), and DNS. https://github.com/BishopFox/sliver
* **EvilOSX** An evil RAT (Remote Administration Tool) for macOS / OS X. https://github.com/Marten4n6/EvilOSX
* **EggShell** is a post exploitation surveillance tool written in Python. It gives you a command line session with extra functionality between you and a target machine. https://github.com/neoneggplant/EggShell

### Staging
* **Rapid Attack Infrastructure (RAI)** Red Team Infrastructure... Quick... Fast... Simplified
One of the most tedious phases of a Red Team Operation is usually the infrastructure setup. This usually entails
a teamserver or controller, domains, redirectors, and a Phishing server. https://github.com/obscuritylabs/RAI
* **Red Baron** is a set of modules and custom/third-party providers for Terraform which tries to automate creating resilient, disposable, secure and agile infrastructure for Red Teams. https://github.com/byt3bl33d3r/Red-Baron
* **EvilURL** generate unicode evil domains for IDN Homograph Attack and detect them. https://github.com/UndeadSec/EvilURL
* **Domain Hunter** checks expired domains, bluecoat categorization, and Archive.org history to determine good candidates for phishing and C2 domain names. https://github.com/threatexpress/domainhunter
* **PowerDNS** is a simple proof of concept to demonstrate the execution of PowerShell script using DNS only. https://github.com/mdsecactivebreach/PowerDNS
* **Chameleon** a tool for evading Proxy categorisation. https://github.com/mdsecactivebreach/Chameleon
* **CatMyFish** Search for categorized domain that can be used during red teaming engagement. Perfect to setup whitelisted domain for your Cobalt Strike beacon C&C. https://github.com/Mr-Un1k0d3r/CatMyFish
* **DomainFrontDiscover** Scripts and results for finding domain frontable CloudFront domains. https://github.com/peewpw/DomainFrontDiscover
* **Automated Empire Infrastructure** https://github.com/bneg/RedTeam-Automation
* **Serving Random Payloads** with NGINX. https://gist.github.com/jivoi/a33ace2e25515a31aa2ffbae246d98c9
* **meek** is a blocking-resistant pluggable transport for Tor. It encodes a
data stream as a sequence of HTTPS requests and responses. https://github.com/arlolra/meek
* **CobaltStrike-ToolKit** Some useful scripts for CobaltStrike. https://github.com/killswitch-GUI/CobaltStrike-ToolKit


## Lateral Movement
Lateral movement is a means to an end; a technique used to identify, gain access to and exfiltrate sensitive data.
* **CrackMapExec** is a swiss army knife for pentesting networks. https://github.com/byt3bl33d3r/CrackMapExec
* **PowerLessShell** rely on MSBuild.exe to remotely execute PowerShell scripts and commands without spawning powershell.exe. https://github.com/Mr-Un1k0d3r/PowerLessShell
* **GoFetch** is a tool to automatically exercise an attack plan generated by the BloodHound application.
 https://github.com/GoFetchAD/GoFetch
* **ANGRYPUPPY** a bloodhound attack path automation in CobaltStrike. https://github.com/vysec/ANGRYPUPPY
* **DeathStar** is a Python script that uses Empire's RESTful API to automate gaining Domain Admin rights in Active Directory environments using a variety of techinques. https://github.com/byt3bl33d3r/DeathStar
* **SharpHound** C# Rewrite of the BloodHound Ingestor. https://github.com/BloodHoundAD/SharpHound
* **BloodHound.py** is a Python based ingestor for BloodHound, based on Impacket. https://github.com/fox-it/BloodHound.py
* **NetRipper** is a post exploitation tool targeting Windows systems which uses API hooking in order to intercept network traffic and encryption related functions from a low privileged user, being able to capture both plain-text traffic and encrypted traffic before encryption/after decryption. https://github.com/NytroRST/NetRipper
* **LethalHTA** Lateral Movement technique using DCOM and HTA. https://github.com/codewhitesec/LethalHTA
* **Invoke-PowerThIEf** an Internet Explorer Post Exploitation library. https://github.com/nettitude/Invoke-PowerThIEf
* **Responder** is a LLMNR, NBT-NS and MDNS poisoner, with built-in HTTP/SMB/MSSQL/FTP/LDAP rogue authentication server supporting NTLMv1/NTLMv2/LMv2, Extended Security NTLMSSP and Basic HTTP authentication. https://github.com/SpiderLabs/Responder
* **SessionGopher** is a PowerShell tool that uses WMI to extract saved session information for remote access tools such as WinSCP, PuTTY, SuperPuTTY, FileZilla, and Microsoft Remote Desktop. It can be run remotely or locally. https://github.com/fireeye/SessionGopher
* **PowerSploit** is a collection of Microsoft PowerShell modules that can be used to aid penetration testers during all phases of an assessment. https://github.com/PowerShellMafia/PowerSploit
* **Nishang** is a framework and collection of scripts and payloads which enables usage of PowerShell for offensive security, penetration testing and red teaming. Nishang is useful during all phases of penetration testing. https://github.com/samratashok/nishang
* **Inveigh** is a Windows PowerShell LLMNR/mDNS/NBNS spoofer/man-in-the-middle tool. https://github.com/Kevin-Robertson/Inveigh
* **PowerUpSQL** a PowerShell Toolkit for Attacking SQL Server. https://github.com/NetSPI/PowerUpSQL
* **MailSniper** is a penetration testing tool for searching through email in a Microsoft Exchange environment for specific terms (passwords, insider intel, network architecture information, etc.). https://github.com/dafthack/MailSniper
* **WMIOps** is a powershell script that uses WMI to perform a variety of actions on hosts, local or remote, within a Windows environment. It's designed primarily for use on penetration tests or red team engagements. https://github.com/ChrisTruncer/WMIOps
* **Mimikatz** is an open-source utility that enables the viewing of credential information from the Windows lsass. https://github.com/gentilkiwi/mimikatz
* **LaZagne** project is an open source application used to retrieve lots of passwords stored on a local computer. https://github.com/AlessandroZ/LaZagne
* **mimipenguin** a tool to dump the login password from the current linux desktop user. Adapted from the idea behind the popular Windows tool mimikatz. https://github.com/huntergregal/mimipenguin
* **PsExec** is a light-weight telnet-replacement that lets you execute processes on other systems, complete with full interactivity for console applications, without having to manually install client software. https://docs.microsoft.com/en-us/sysinternals/downloads/psexec
* **KeeThief** allows for the extraction of KeePass 2.X key material from memory, as well as the backdooring and enumeration of the KeePass trigger system. https://github.com/HarmJ0y/KeeThief
* **PSAttack** combines some of the best projects in the infosec powershell community into a self contained custom PowerShell console. https://github.com/jaredhaight/PSAttack
* **Internal Monologue Attack** Retrieving NTLM Hashes without Touching LSASS. https://github.com/eladshamir/Internal-Monologue
* **Impacket** is a collection of Python classes for working with network protocols. Impacket is focused on providing low-level programmatic access to the packets and for some protocols (for instance NMB, SMB1-3 and MS-DCERPC) the protocol implementation itself. https://github.com/CoreSecurity/impacket
* **icebreaker** gets plaintext Active Directory credentials if you're on the internal network but outside the AD environment. https://github.com/DanMcInerney/icebreaker
* **Living Off The Land Binaries and Scripts (and now also Libraries)** The goal of these lists are to document every binary, script and library that can be used for other purposes than they are designed to. https://github.com/api0cradle/LOLBAS
* **WSUSpendu** for compromised WSUS server to extend the compromise to clients. https://github.com/AlsidOfficial/WSUSpendu
* **Evilgrade** is a modular framework that allows the user to take advantage of poor upgrade implementations by injecting fake updates. https://github.com/infobyte/evilgrade
* **RedSnarf** is a pen-testing / red-teaming tool for Windows environments. https://github.com/nccgroup/redsnarf
* **HoneypotBuster** Microsoft PowerShell module designed for red teams that can be used to find honeypots and honeytokens in the network or at the host. https://github.com/JavelinNetworks/HoneypotBuster
* **PAExec** lets you launch Windows programs on remote Windows computers without needing to install software on the remote computer first. https://www.poweradmin.com/paexec/

## Establish Foothold
* **Tunna** is a set of tools which will wrap and tunnel any TCP communication over HTTP. It can be used to bypass network restrictions in fully firewalled environments. https://github.com/SECFORCE/Tunna
* **reGeorg** the successor to reDuh, pwn a bastion webserver and create SOCKS proxies through the DMZ. Pivot and pwn. https://github.com/sensepost/reGeorg
* **Blade** is a webshell connection tool based on console, currently under development and aims to be a choice of replacement of Chooper. https://github.com/wonderqs/Blade
* **TinyShell** Web Shell Framework. https://github.com/threatexpress/tinyshell
* **PowerLurk** is a PowerShell toolset for building malicious WMI Event Subsriptions. https://github.com/Sw4mpf0x/PowerLurk
* **DAMP** The Discretionary ACL Modification Project: Persistence Through Host-based Security Descriptor Modification.
https://github.com/HarmJ0y/DAMP

## Privilege Escalation
Privilege escalation is the act of exploiting a bug, design flaw or configuration oversight in an operating system or software application to gain elevated access to resources that are normally protected from an application or user. 
* **PowerView** is a PowerShell tool to gain network situational awareness on Windows domains. https://github.com/PowerShellMafia/PowerSploit/blob/master/Recon/PowerView.ps1
* **Get-GPPPassword** Retrieves the plaintext password and other information for accounts pushed through Group Policy Preferences. https://github.com/PowerShellMafia/PowerSploit/blob/master/Exfiltration/Get-GPPPassword.ps1
* **Invoke-ACLpwn** is a tool that automates the discovery and pwnage of ACLs in Active Directory that are unsafe configured. https://github.com/fox-it/Invoke-ACLPwn
* **BloodHound** uses graph theory to reveal the hidden and often unintended relationships within an Active Directory environment. https://github.com/BloodHoundAD/BloodHound
* **PyKEK** (Python Kerberos Exploitation Kit), a python library to manipulate KRB5-related data. https://github.com/SecWiki/windows-kernel-exploits/tree/master/MS14-068/pykek
* **Grouper** a PowerShell script for helping to find vulnerable settings in AD Group Policy.
https://github.com/l0ss/Grouper
* **ADRecon** is a tool which extracts various artifacts (as highlighted below) out of an AD environment in a specially formatted Microsoft Excel report that includes summary views with metrics to facilitate analysis. https://github.com/sense-of-security/ADRecon
* **ADACLScanner** one script for ACL's in Active Directory. https://github.com/canix1/ADACLScanner
* **ACLight** a useful script for advanced discovery of Domain Privileged Accounts that could be targeted - including Shadow Admins. https://github.com/cyberark/ACLight
* **LAPSToolkit** a tool to audit and attack LAPS environments. https://github.com/leoloobeek/LAPSToolkit
* **PingCastle** is a free, Windows-based utility to audit the risk level of your AD infrastructure and check for vulnerable practices. https://www.pingcastle.com/download
* **RiskySPNs** is a collection of PowerShell scripts focused on detecting and abusing accounts associated with SPNs (Service Principal Name). https://github.com/cyberark/RiskySPN
* **Mystique** is a PowerShell tool to play with Kerberos S4U extensions, this module can assist blue teams to identify risky Kerberos delegation configurations as well as red teams to impersonate arbitrary users by leveraging KCD with Protocol Transition. https://github.com/machosec/Mystique
* **Rubeus** is a C# toolset for raw Kerberos interaction and abuses. It is heavily adapted from Benjamin Delpy's Kekeo project. https://github.com/GhostPack/Rubeus
* **kekeo** is a little toolbox I have started to manipulate Microsoft Kerberos in C (and for fun). https://github.com/gentilkiwi/kekeo

### Local Escalation
* **UACMe** is an open source assessment tool that contains many methods for bypassing Windows User Account Control on multiple versions of the operating system. https://github.com/hfiref0x/UACME
* **windows-kernel-exploits** a collection windows kernel exploit. https://github.com/SecWiki/windows-kernel-exploits
* **PowerUp** aims to be a clearinghouse of common Windows privilege escalation vectors that rely on misconfigurations. https://github.com/PowerShellMafia/PowerSploit/blob/master/Privesc/PowerUp.ps1
* **The Elevate Kit** demonstrates how to use third-party privilege escalation attacks with Cobalt Strike's Beacon payload. https://github.com/rsmudge/ElevateKit
* **Sherlock** a powerShell script to quickly find missing software patches for local privilege escalation vulnerabilities.
 https://github.com/rasta-mouse/Sherlock

## Data Exfiltration
Data exfiltration occurs when malware and/or a malicious actor carries out an unauthorized data transfer from a computer. It is also commonly called data extrusion or data exportation. Data exfiltration is also considered a form of data theft.
* **CloakifyFactory** & the Cloakify Toolset - Data Exfiltration & Infiltration In Plain Sight; Evade DLP/MLS Devices; Social Engineering of Analysts; Defeat Data Whitelisting Controls; Evade AV Detection. https://github.com/TryCatchHCF/Cloakify
* **DET** (is provided AS IS), is a proof of concept to perform Data Exfiltration using either single or multiple channel(s) at the same time. https://github.com/sensepost/DET
* **DNSExfiltrator** allows for transfering (exfiltrate) a file over a DNS request covert channel. This is basically a data leak testing tool allowing to exfiltrate data over a covert channel. https://github.com/Arno0x/DNSExfiltrator
* **PyExfil** a Python Package for Data Exfiltration. https://github.com/ytisf/PyExfil
* **Egress-Assess** is a tool used to test egress data detection capabilities. https://github.com/ChrisTruncer/Egress-Assess
* **Powershell RAT** python based backdoor that uses Gmail to exfiltrate data as an e-mail attachment. https://github.com/Viralmaniar/Powershell-RAT

### Software For Team Communication
* **RocketChat** is free, unlimited and open source. Replace email & Slack with the ultimate team chat software solution. https://rocket.chat
* **Etherpad** is an open source, web-based collaborative real-time editor, allowing authors to simultaneously edit a text document https://etherpad.net

### Log Aggregation
Log aggregation is a valuable tool, but it isn't normally a good tool for time-series data. A log aggregation system is a great place for collecting event data. These are irregular activities that are significant. An example might be access logs for a web service.
* **RedELK** Red Team's SIEM - easy deployable tool for Red Teams used for tracking and alarming about Blue Team activities as well as better usability in long term operations. https://github.com/outflanknl/RedELK/
* **CobaltSplunk** Splunk Dashboard for CobaltStrike logs. https://github.com/vysec/CobaltSplunk
* **Red Team Telemetry** A collection of scripts and configurations to enable centralized logging of red team infrastructure. https://github.com/ztgrace/red_team_telemetry
* **Elastic for Red Teaming** Repository of resources for configuring a Red Team SIEM using Elastic. https://github.com/SecurityRiskAdvisors/RedTeamSIEM

## Forensics
* **Autopsy** A digital forensics platform and graphical interface to The Sleuth Kit and other digital forensics tools · sleuthkit - A library and collection of command-line digital forensics tools · EnCase - The shared technology within a suite of digital investigations products by Guidance Software https://www.sleuthkit.org/autopsy/

## Cryptography

* **xortool** A tool to analyze multi-byte XOR cipher · John the Ripper - A fast password cracker · Aircrack - Aircrack is 802.11 WEP and WPA-PSK keys cracking program. https://github.com/hellman/xortool

## Wargame

* **OverTheWire** - Semtex · OverTheWire - Vortex · OverTheWire - Drifter · pwnable.kr - Provide various pwn challenges regarding system security · Exploit Exercises - Nebula · SmashTheStack

## Reverse Engineering
* **Reversing.kr** This site tests your ability to Cracking & Reverse Code Engineering· http://reversing.kr/
* **Crackmes.de** The world first and largest community website for crackmes and reversemes. http://crackmes.de/
* **Hack This Site** A free, safe and legal training ground for hackers to test and expand their hacking skills. https://www.hackthissite.org/

## DLL Architecture
Dynamic linking is a mechanism that links applications to libraries at run time. The libraries remain in their own files and are not copied into the executable files of the applications. DLLs link to an application when the application is run, rather than when it is created.
### Kernel32.dll
This is a very common DLL that contains core functionality, such as access and manipulation of memory, files, and hardware. 
### Advapi32.dll
This DLL provides access to advanced core Windows components such as the Service Manager and Registry.
### User32.dll
This DLL contains all the user-interface components, such as buttons, scroll bars, and components for controlling and responding to user actions. 
### Gdi32.dll
This DLL contains functions for displaying and manipulating graphics.
### Ntdll.dll
This DLL is the interface to the Windows kernel. 
### WSock32.dll and Ws2_32.dll
These are networking DLLs. A program that accesses either of these most likely connects to a network or performs network-related tasks.
### Wininet.dll
This DLL contains higher-level networking functions. 

## Best Tools
* **Dissasembler** – IDA Pro
* **Debugger** – OllyDbg, WinDbg
* **System Monitor** – Process Monitor, RegShot. Process Explorer
* **Network Monitor** – TCP View, Wireshark
* **Packer Identifier** – PEID
* **Unpacking Tools** – Qunpack. GUNPacker
* **Binary Analysis Tools** – PE Explorer, Malcode Analysts Pack
* **Code Analysis Tools** – LordPE, ImpRec

## X86 Architecture
The x86 architecture is an instruction set architecture. It is a set of computer processors that were developed by the Intel Corporation. x86 architecture defines how a processor handles and executes different instructions on a computer by setting standards on application execution.

* **EAX:** Extended Accumulator Register
* **EBX:** Extended Base Register
* **ECD:** Extended Counter Register
* **EDX:** Extended Data Register 
* **ESI:** Extended Source Index 
* **EDI:** Extended Destination Index 
* **EBP:** Extended Base Pointer
* **ESP:** Extended Stack Pointer

The POP instruction pops a value or memory address which is the name in the stack.  Additionally it also increments the stack pointer to point to the new top of the stack. The PUSH instruction pushes a value to the stack and decrements the stack pointer to point to the new top.

## References
* **MITRE’s ATT&CK™** is a curated knowledge base and model for cyber adversary behavior, reflecting the various phases of an adversary’s lifecycle and the platforms they are known to target. https://attack.mitre.org/wiki/Main_Page
* **Cheat Sheets** for various projects (Beacon/Cobalt Strike,PowerView, PowerUp, Empire, and PowerSploit). https://github.com/HarmJ0y/CheatSheets
* **PRE-ATT&CK** Adversarial Tactics, Techniques & Common Knowledge for Left-of-Exploit. https://attack.mitre.org/pre-attack/index.php/Main_Page
* **Adversary OPSEC** consists of the use of various technologies or 3rd party services to obfuscate, hide, or blend in with accepted network traffic or system behavior. https://attack.mitre.org/pre-attack/index.php/Adversary_OPSEC
* **Adversary Emulation Plans** To showcase the practical use of ATT&CK for offensive operators and defenders, MITRE created Adversary Emulation Plans. https://attack.mitre.org/wiki/Adversary_Emulation_Plans
* **Red-Team-Infrastructure-Wiki** Wiki to collect Red Team infrastructure hardening resources. https://github.com/bluscreenofjeff/Red-Team-Infrastructure-Wiki
* **Advanced Threat Tactics – Course and Notes** This is a course on red team operations and adversary simulations. https://blog.cobaltstrike.com/2015/09/30/advanced-threat-tactics-course-and-notes
* **Red Team Tips** as posted by @vysecurity on Twitter. https://vincentyiu.co.uk/red-team-tips
* **Awesome Red Teaming** List of Awesome Red Team / Red Teaming Resources. https://github.com/yeyintminthuhtut/Awesome-Red-Teaming
* **APT & CyberCriminal Campaign Collection** This is a collection of APT and CyberCriminal campaigns. Please fire issue to me if any lost APT/Malware events/campaigns. https://github.com/CyberMonitor/APT_CyberCriminal_Campagin_Collections
* **ATT&CK for Enterprise Software** is a generic term for custom or commercial code, operating system utilities, open-source software, or other tools used to conduct behavior modeled in ATT&CK. https://attack.mitre.org/wiki/Software
* **Planning a Red Team exercise** This document helps inform red team planning by contrasting against the very specific red team style described in Red Teams. https://github.com/magoo/redteam-plan
* **Awesome Lockpicking** a curated list of awesome guides, tools, and other resources related to the security and compromise of locks, safes, and keys. https://github.com/meitar/awesome-lockpicking
* **Awesome Threat Intelligence** a curated list of awesome Threat Intelligence resources. https://github.com/hslatman/awesome-threat-intelligence
* **APT Notes** Need some scenario? APTnotes is a repository of publicly-available papers and blogs (sorted by year) related to malicious campaigns/activity/software that have been associated with vendor-defined APT (Advanced Persistent Threat) groups and/or tool-sets. https://github.com/aptnotes/data
* **TIBER-EU FRAMEWORK** The European Framework for Threat Intelligence-based Ethical Red Teaming (TIBER-EU), which is the first Europe-wide framework for controlled and bespoke tests against cyber attacks in the financial market. http://www.ecb.europa.eu/pub/pdf/other/ecb.tiber_eu_framework.en.pdf
* **CBEST Implementation Guide** CBEST is a framework to deliver controlled, bespoke, intelligence-led cyber security tests. The tests replicate behaviours of threat actors, assessed by the UK Government and commercial intelligence providers as posing a genuine threat to systemically important financial institutions.
https://www.crest-approved.org/wp-content/uploads/2014/07/CBEST-Implementation-Guide.pdf
* **Red Team: Adversarial Attack Simulation Exercise Guidelines for the Financial Industry in Singapore** The Association of Banks in Singapore (ABS), with support from the Monetary Authority of Singapore (MAS), has developed a set of cybersecurity assessment guidelines today to strengthen the cyber resilience of the financial sector in Singapore. Known as the Adversarial Attack Simulation Exercises (AASE) Guidelines or “Red Teaming” Guidelines, the Guidelines provide financial institutions (FIs) with best practices and guidance on planning and conducting Red Teaming exercises to enhance their security testing.
https://abs.org.sg/docs/library/abs-red-team-adversarial-attack-simulation-exercises-guidelines-v1-06766a69f299c69658b7dff00006ed795.pdf
* **Acunetix. What is Google Hacking?** Available at https://www.acunetix.com/websitesecurity/google-hacking/ (12/06/2016)
* **Czumak, M. (2014). Passive Reconnaissance.** Available at http://www.securitysift.com/passive-reconnaissance/ (12/06/2016)
* **fr4nc1stein (2015). Google Dorks:** An Easy Way of Hacking. Available at https://www.cybrary.it/0p3n/google-dorks-easy-way-of-hacking/ (12/06/2016)
* **Hack Cave. The Basics of Penetration Testing.** vailable at http://www.hackcave.net/2015/11/the-basics-of-penetration-testing.html (12/06/2016)
* **Gianchandani, P. (2011). DNS Hacking (Beginner to Advanced).** Available at http://resources.infosecinstitute.com/dns-hacking/ (12/06/2016)
* **Google Hacker (2015). Using Google as a website vulnerability scanner.** Available at http://www.ghackingdb.com/using-google-as-a-website-vulnerability-scanner/ (12/06/2016)
* **Gupta, T. (2010). 5 penetration test tools to secure your network.** Available at www.computerweekly.com/tip/5-penetration-test-tools-to-secure-your-network (12/06/2016)
* **Rumy, S. (2016). Enumerating DNS records with DNSenum Tool in Kali Linux.** Available at http://rumyittips.com/enumerating-dns-records-with-dnsenum-tool-in-kali-linux/ (12/06/2016)
* **Tech-FAQ (2016). Reverse DNS.** Available at http://www.tech-faq.com/reverse-dns.html (12/06/2016)
* **Tech-FAQ (2016). How to Perform a DNS Lookup.** Available at http://www.tech-faq.com/how-to-perform-a-dns-lookup.html (12/06/2016)
* **True Demon (2015). The Hacker Ethos.** Available at https://books.google.bg/books?id=-xhPCwAAQBAJ&pg=PT180&lpg=PT180&dq=eavesdropping+information+gathering&source=bl&ots=wYqDq-XtpT&sig=uYOpP8XI9-IVgm_DJZbCWqIxgGI&hl=bg&sa=X&ved=0ahUKEwiqm-W4vKrNAhUDtBQKHZkoAus4ChDoAQgzMAI#v=onepage&q=eavesdropping%20information%20gathering&f=false (12/06/2016)
* **Wing (2014). 15 Penetration Testing Tools-Open Source.** Available at http://securitywing.com/15-penetration-testing-tools-open-source/ (12/06/2016)
* **Vines, R. (2016). Penetration testing reconnaissance — Footprinting, scanning and enumerating.** Available at http://searchitchannel.techtarget.com/tip/Penetration-testing-reconnaissance-Footprinting-scanning-and-enumerating (12/06/2016)

## License
[![License: GPL v3](https://img.shields.io/badge/License-GPL%20v3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)
