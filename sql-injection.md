
# Name

SQL Injection

# Severity

High

# CVSS Score

8.6

# CVSS Vector

CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:C/C:H/I:N/A:N

# CWE ID

CWE-89

# CWE NAME 

SQL Injection

# Affected Compliance

OWASP Top 10: A1

PCI-DSS: 6.5.1

# Description

SQL Injections are the most common form of injections because SQL databases are very popular in dynamic web applications. This vulnerability allows an attacker to tamper existing SQL queries performed by the web application. Depending on the queries, the attacker might be able to access, modify or even destroy data from the database.

Since databases are commonly used to store private data, such as authentication information, personal user data and site content, if an attacker gains access to it, the consequences are typically very severe, ranging from defacement of the web application to users data leakage or loss, or even full control of the web application or database server.

# Generic How-to fix

To fix an SQL Injection you should use Prepared Statements. If an application exclusively uses prepared statements, the developer can be sure that no SQL injection will occur.
Prepared Statements can be thought of as a kind of compiled template for the SQL that an application wants to run, that can be customized using variable parameters.

As an added bonus, if you're executing the same query several times, then it'll be even faster than when you're not using prepared statements. This is because when using prepared statements, the query needs to be parsed (prepared) only once, but can be executed multiple times with the same or different parameters. 
