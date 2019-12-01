### Getting ROOT/Exploiting

Weak Credentials: S3crets are no fun! Using credentials that are vendor set, or easily guessable.

Apache Tomcat Upload Manager: Using Metasploit to gain access to the machine.

Tools

NMAP: Network mapping tool that allows you to scan for open ports, services, and operating systems to list a few features. It also has scripts that allow for much more in-depth enumeration.

Metasploit: Metasploit, a tool maintained by Rapid 7, is thought of as a pentesters toolbelt. There are so many uses for Metasploit that BOOKS have been written about the tool.

Methodology

First things first — Scan the machine!

    > nmap -sC -sV 10.10.10.95 -oA
