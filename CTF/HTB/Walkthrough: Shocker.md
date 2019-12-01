[![sd](https://miro.medium.com/max/549/0*fWGNFg_-JPZjoRUL.jpg "sd")](dsd "sd")

 ### Getting ROOT/Exploiting
 
/CGI-Bin — Metasploit was used to gain access to the machine.

#### Tools

NMAP: Network mapping tool that allows you to scan for open ports, services, and operating systems to list a few features. It also has scripts that allow for much more in-depth enumeration.

Metasploit: Metasploit, a tool maintained by Rapid 7, is thought of as a pentesters toolbelt. There are so many uses for Metasploit that BOOKS have been written about the tool.

Dirb: Performing directory traversal by scanning web sites. Think of it as a web-based dictionary attack.

Curl: Atool to transfer data from or to a server, using one of the supported protocols. The command is designed to work without user interaction.

#### Vulnerabilities/Exploits

Shellshock — a security bug causing Bash to execute commands from environment variables unintentionally.

Methodology

Scanning the machine is the first step in our ad-hoc methodology. Scanning allows us to see what services are running on the machine. Below is the command that was run against the machine.

[![sd](https://miro.medium.com/max/1198/0*ZZ853tcwKIpN1aI8 "sd")](dsd "sd")

ports 80 and 2222 were discovered. since port 80 supports HTTP, the next step is to do some directory traversal with Dirb, and also bring up the web page.

The main page displays a screen saying “don’t bug me.” viewing the source code didn’t show anything, so next it’s time to turn to the dirb search.


[![sd](https://miro.medium.com/max/1070/0*ys52ZJe5pbZrIUAq "sd")](dsd "sd")

The path “cgi-bin” was discovered. CGI-bin is used to house scripts that will interact with a Web browser to provide functionality for a Web page or website.

Next up, seeing what CGI-bin is all about. Check out some of its uses here: https://serverpilot.io/docs/how-to-create-a-cgi-bin-directory

Knowing there is a test.sh, it seems likely that there be more directories with info labeled “.sh”. So the next order of ops is to do another dirb scan on the cgi-bin folder that looks specifically for files that have “.sh”

[![sd](https://miro.medium.com/max/1284/0*a1kCR64Ht5MVZrTM "sd")](dsd "sd")

Looks like “user.sh” is found. Personally, I wanted to use curl to see if it would give a 200 code.

[![sd](  https://miro.medium.com/max/1536/0*d4XXT8kwz9WT-CZX   "sd")](dsd "sd")

At this point, it’s time to do some testing and see what we can get. Being that the box name is Shocker, and CGI-Bin is present — it’s concluded that shellshock is a possibility, so we move into exploiting it with Metasploit.

#### EXPLOITATION

Using Metasploits Shellshock exploit (See Below), you can successfully get a low privilege shell on the box and compromise the account “shelly”.

[![sd]( https://miro.medium.com/max/1600/0*fwG6JytMZZghz2Bd   "sd")](dsd "sd")

Some things to take note are the “TARGETURI”. Ensure that is set to “cgi-bin/user.sh”.

[![sd]( https://miro.medium.com/max/1600/0*AaQbi-O8oJTVNefB   "sd")](dsd "sd")

Boom! Got a shell. Now do some lateral movement and get the user flag.

[![sd]( https://miro.medium.com/max/896/0*JjO2laLE0Pzqx3P-   "sd")](dsd "sd")

[![sd]( https://miro.medium.com/max/952/0*ITV1IDnebylwKlYa   "sd")](dsd "sd")

As you can see, you won't be able to get into the root directory. So you’ll need to get some info to escalate your privileges. Make sure you “drop” down into a Linux shell. Simply type “shell” in your meterpreter session.

    To get a better interactive shell, type “/bin/sh -i”.

No password needed for perl commands.


Knowing that no password is needed for perl commands — the following script, “sudo perl -e ‘ exec “/bin/sh”’, will allow you to get root — ultimately leading you to paydirt: root.txt

[![sd]( https://miro.medium.com/max/800/0*KzvtozAgIvUs634c  "sd")](dsd "sd")
