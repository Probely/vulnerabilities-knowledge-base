
# Name

Log file disclosure

# Severity

Low

# CVSS Score

5.3

# CVSS Vector

CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:L/I:N/A:N

# CWE ID

CWE-200

# CWE NAME 

Exposure of Sensitive Information to an Unauthorized Actor

# Affected Compliance

OWASP Top 10: A6

# Description

A log file was found in the application document root, meaning it is available for viewing to anyone browsing through the application.

Since the location of the log file is easy to guess or it is a well-known path used for logs, it is very easy for an attacker to find it and take advantage of sensitive data that it may contain. Depending on the information present in the log, access to it may increase the probability of exploitation of other vulnerabilities, or even facilitate the take over of user accounts.

# Generic How-to fix

To fix this problem, change the location of the log file at the application configuration. You can, and should, also prevent your web server from serving files with the extension `.log`. This will add an extra layer of protection in the case any log is left in the document root.
