# SQL Injection

### What is SQL injection (SQLi)?

SQL injection is a web security vulnerability that allows an attacker to interfere with the queries that an application makes to its database. It generally allows an attacker to view data that they are not normally able to retrieve. This might include data belonging to other users, or any other data that the application itself is able to access. In many cases, an attacker can modify or delete this data, causing persistent changes to the application’s content or behavior.

In some situations, an attacker can escalate an SQL injection attack to compromise the underlying server or other back-end infrastructure, or perform a denial-of-service attack.

### SQL Injection Type :

|    SQL Injection Type        | Description                     
|----------------|-------------------------------|
|In-band SQLi (Classic SQLi)|In-band SQL Injection is the most common and easy-to-exploit of SQL Injection attacks. In-band SQL Injection occurs when an attacker is able to use the same communication channel to both launch the attack and gather results. The two most common types of in-band SQL Injection are Error-based SQLi and Union-based SQLi. |    
|Error-based SQLi          |Error-based SQLi is an in-band SQL Injection technique that relies on error messages thrown by the database server to obtain information about the structure of the database. In some cases, error-based SQL injection alone is enough for an attacker to enumerate an entire database.| 
|Union-based SQLi         |Union-based SQLi is an in-band SQL injection technique that leverages the UNION SQL operator to combine the results of two or more SELECT statements into a single result which is then returned as part of the HTTP response.|
|Inferential SQLi (Blind SQLi)|Inferential SQL Injection, unlike in-band SQLi, may take longer for an attacker to exploit, however, it is just as dangerous as any other form of SQL Injection. In an inferential SQLi attack, no data is actually transferred via the web application and the attacker would not be able to see the result of an attack in-band (which is why such attacks are commonly referred to as “blind SQL Injection attacks”). Instead, an attacker is able to reconstruct the database structure by sending payloads, observing the web application’s response and the resulting behavior of the database server. The two types of inferential SQL Injection are Blind-boolean-based SQLi and Blind-time-based SQLi.|
|Boolean-based (content-based) Blind SQLi |Boolean-based SQL Injection is an inferential SQL Injection technique that relies on sending an SQL query to the database which forces the application to return a different result depending on whether the query returns a TRUE or FALSE result. Depending on the result, the content within the HTTP response will change, or remain the same. This allows an attacker to infer if the payload used returned true or false, even though no data from the database is returned.|
|Time-based Blind SQLi |Time-based SQL Injection is an inferential SQL Injection technique that relies on sending an SQL query to the database which forces the database to wait for a specified amount of time (in seconds) before responding. The response time will indicate to the attacker whether the result of the query is TRUE or FALSE. epending on the result, an HTTP response will be returned with a delay, or returned immediately. This allows an attacker to infer if the payload used returned true or false, even though no data from the database is returned.|
|Out-of-band SQLi|Out-of-band SQL Injection is not very common, mostly because it depends on features being enabled on the database server being used by the web application. Out-of-band SQL Injection occurs when an attacker is unable to use the same channel to launch the attack and gather results. Out-of-band techniques, offer an attacker an alternative to inferential time-based techniques, especially if the server responses are not very stable (making an inferential time-based attack unreliable).|
| Voice Based Sql Injection | It is a sql injection attack method that can be applied in applications that provide access to databases with voice command. An attacker could pull information from the database by sending sql queries with sound. |

### How it works
An attacker may use malformed data in a request, using a query-field, a search-box or login-fields to abuse unsafe SQL-code and inject malicious SQL-code on the server. This can be abused to gain access to user accounts, retrieve data from or change data in the database of the application.

### Example
For example, consider a simple login-form:

![](https://raw.githubusercontent.com/brampat/security/master/techniques/sql-injection/login-form.png)

Now consider the following code to validate the credentials:

```SQL
SELECT U.USERNAME FROM USERS U WHERE U.USERNAME = '" + $_POST['username'] + "' AND U.PASSWORD = '" + $_POST['password'] + "' 
```

When used as intended, this statement will result in the following example query:

```SQL
SELECT U.USERNAME FROM USERS U WHERE U.USERNAME = 'foo' AND U.PASSWORD = 'bar' 
```

If there is a user with username 'foo' and password 'bar', this query returns a single result and the user is authenticated. But consider the following malicious input:

Username: ```admin'--```
Password: ```doesnt matter```

This will result in the following SQL statement
```SQL
SELECT U.USERNAME FROM USERS U WHERE U.USERNAME = 'admin'--' AND U.PASSWORD = 'doesnt matter' 
```

The password-check is now commented out, including the hardcoded end-of-string quote directly following the username param. This will result in the query just checking for the corresponding username and logging in as that user.
Since the query is constructed using String concatenation, with malicious input, the attacker can re-structure the SQL-statement to perform the unintended behavior.


## Blind SQL Injection techniques

Mostly, web-application will hide output of the actual SQL-query. 
This way, you have no direct feedback of the database-result of an SQL-Injection attack.
There are however, other ways to dissect and discover the structure and content of a database.
While these methods are complex and very time-consuming when executed manually, there are tools that fully automate these kinds of attacks.

### Basics
Blind SQL injection abuses different techniques to understand valid or invalid queries
the fact that a valid query will return a different result as an invalid query.
For instance, the following query may result in an actual result page:

```
http://newspaper.com/items.php?id=2
// results in:
SELECT title, description, body FROM items WHERE ID = 2
```

While this page may result in an error-page:
```
http://newspaper.com/items.php?id=2 and 1=2
// results in:
SELECT title, description, body FROM items WHERE ID = 2 and 1=2
```

# Sources
* [SQL injection for dummies](https://www.youtube.com/watch?v=ciNHn38EyRc)
* [SQL injection cheat sheet](http://pentestmonkey.net/cheat-sheet/sql-injection/mysql-sql-injection-cheat-sheet)
* [SQL and NoSQL injection](https://ckarande.gitbooks.io/owasp-nodegoat-tutorial/content/tutorial/a1_-_sql_and_nosql_injection.html)
* [Acunetix](https://www.acunetix.com/blog/articles/exploiting-sql-injection-example/) full step-by-step exploit with SQL-injection
* [OWASP](https://www.owasp.org/index.php/Blind_SQL_Injection)
* [Acunetix](https://www.acunetix.com/websitesecurity/blind-sql-injection/)
* [Time-base blind SQLi](http://www.sqlinjection.net/time-based/)
* [Exploiting a tricky blind SQL injection](https://www.noob.ninja/2019/07/exploiting-tricky-blind-sql-injection.html)
* [SQL Injection out of band exploitation](https://www.gracefulsecurity.com/sql-injection-out-of-band-exploitation/)
* [SQL Injection filter evasion with sqlmap](https://www.gracefulsecurity.com/sql-injection-filter-evasion/)
* [Introduction to SQLMap](https://www.gracefulsecurity.com/introduction-to-sqlmap/)

## SQL injection fun stuff
* [Company name](https://beta.companieshouse.gov.uk/company/10542519) with SQL injection
