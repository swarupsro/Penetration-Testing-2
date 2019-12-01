[![sd](https://miro.medium.com/max/527/0*60Coa2PkVezUtKGU.png "sd")](dsd "sd")
### Getting ROOT/Exploiting

Weak Credentials: S3crets are no fun! Using credentials that are vendor set, or easily guessable.

Apache Tomcat Upload Manager: Using Metasploit to gain access to the machine.

Tools

NMAP: Network mapping tool that allows you to scan for open ports, services, and operating systems to list a few features. It also has scripts that allow for much more in-depth enumeration.

Metasploit: Metasploit, a tool maintained by Rapid 7, is thought of as a pentesters toolbelt. There are so many uses for Metasploit that BOOKS have been written about the tool.

#### Methodology

First things first — Scan the machine!

    > nmap -sC -sV 10.10.10.95 -oA

You’ll notice from the output of the machine that port 8080 is open. You’ll be prompted by a fancy apache tomcat server. Looking at some directories with dirb (screenshot no included)you’ll find a directory “tomcat-users.xml”. Going to it gives you a 401 error and shows you the credentials to log into the web appliance.

[![https://miro.medium.com/max/1096/0*YPhx4MXgm0ggivRb](https://miro.medium.com/max/1096/0*YPhx4MXgm0ggivRb "https://miro.medium.com/max/1096/0*YPhx4MXgm0ggivRb")](https://miro.medium.com/max/1096/0*YPhx4MXgm0ggivRb "https://miro.medium.com/max/1096/0*YPhx4MXgm0ggivRb")

You can also scan for passwords with METASPLOIT (See screenshot below).

[![sd](https://miro.medium.com/max/582/0*7WGP3ggnuxG_jEAl "sd")](dsd "sd")

#### EXPLOITING

Load up Metasploit and search for tomcat manager exploit!

[![sd](https://miro.medium.com/max/593/0*xvhD4q1hbI0_J-S9 "sd")](dsd "sd")

Set your parameters with the credentials previously found, set the port to 8080, set rhosts to the IP of the jerry machine: EXPLOIT

You should be greated by a lovely meterpreter shell that will give you the leverage to pilfer through the machine as you please.

[![sd](https://miro.medium.com/max/938/0*AONXoUAV1oRtBx_9 "sd")](dsd "sd")

Once you have a terminal, go to the Administration directory located in the Users directory.

[![sd](https://miro.medium.com/max/741/0*pDIjF3KYPIV8qw1w "sd")](dsd "sd")

Then go to the Desktop directory. Here you will find “flags” directory.

[![sd](https://miro.medium.com/max/1600/0*ZZYSG5msLjUSn_rh "sd")](dsd "sd")

Once you have done that, you can download both the user and root flag from your meterpreter shell!
