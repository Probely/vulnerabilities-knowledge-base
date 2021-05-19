
# Name

HTTP TRACE method enabled

# Severity

Low

# CVSS Score

3.7

# CVSS Vector

CVSS:3.0/AV:N/AC:H/PR:N/UI:N/S:U/C:L/I:N/A:N

# CWE ID

CWE-16

# CWE NAME 

Configuration

# Affected Compliance

OWASP Top 10: A6

# Description

The HTTP TRACE method is used for debugging purposes and therefore should not be enabled. This method causes the web server to include a copy of the received request in the response, so one can see exactly what was received by the server.

The request that reaches the server might contain more information than the one sent by the client. Sensitive information, such as HTTP headers with internal IP or authentication tokens, credentials, etc, could have been added by reverse proxies, something that was otherwise invisible to the client. This information can then be used to improve the successful exploitation of other vulnerabilities.

# Generic How-to fix

The HTTP Trace method is a setting configurable at the web server level, thus you can disable it in its configuration file, either globally or per virtual host.

How to disable it is specific to the web server that you are using, and independent of the language of your application. 

For instance, in an Apache server you disable it in the virtual host configuration file, with:
```
    TraceEnable Off
```
