https://www.hackingarticles.in/4-ways-dns-enumeration/

DNS Zone Transfers:

    nslookup -> set type=any -> ls -d xxx.com
    dig axfr xxxx.com @ns1.xxx.com
    dnsrecon -d TARGET -D /usr/share/wordlists/dnsmap.txt -t std --xml ouput.xml // Recon

