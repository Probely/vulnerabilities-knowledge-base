
# Name

Heartbleed

# Severity

High

# CVSS Score

8.8

# CVSS Vector

CVSS:3.0/AV:N/AC:L/PR:N/UI:R/S:U/C:H/I:H/A:H

# CWE ID

CWE-126

# CWE NAME 

Buffer over-read

# Affected Compliance

OWASP Top 10: A9

# Description

Heartbleed is a serious vulnerability in the OpenSSL library, which is used in many software that supports web applications, such as webservers. This vulnerability allows an attacker to steal sensitive information that is in the memory of the servers where OpenSSL is being used.
For instance, Heartbleed can be exploited to steal the private key associated with the certificate the server uses to deliver HTTPS, or even passwords from the users currently using the application.

This vulnerability has the CVE-2014-0160.

# Generic How-to fix

The source of this vulnerability is the OpenSSL library, which is used by your webserver, for instance, to handle SSL/TLS connections.

The solution is to update the OpenSSL library to the most recent version. The first version of OpenSSL where this problem is fixed is 1.0.1g, so ensure that you have at least this version.
