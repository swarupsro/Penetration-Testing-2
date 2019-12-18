https://www.hackingarticles.in/penetration-testing-on-mysql-port-3306/

https://www.hackingarticles.in/mysql-penetration-testing-nmap/

nmap -sV -Pn -vv 10.0.0.1 -p 3306 --script mysql-audit,mysql-databases,mysql-dump-hashes,mysql-empty-password,mysql-enum,mysql-info,mysql-query,mysql-users,mysql-variables,mysql-vuln-cve2012-2122
