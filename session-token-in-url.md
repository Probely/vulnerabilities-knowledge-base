
# Name

Session Token in URL

# Severity

Medium

# CVSS Score

5.9

# CVSS Vector

CVSS:3.0/AV:N/AC:H/PR:N/UI:R/S:U/C:H/I:L/A:N

# CWE ID

CWE-200

# CWE NAME 

Exposure of Sensitive Information to an Unauthorized Actor

# Affected Compliance

OWASP Top 10: A2, A3

PCI-DSS: 6.5.10

# Description

Sensitive information transmitted in the URL may be logged in different locations such as the browser history, the web server logs and any proxy present between the client and the application. It may also be sent to third party sites through the referer header, just by following a link in the application.

It is also easier to inadvertently share the URL with the sensitive information with an accidental copy-paste or by sharing the URL in a social application.

In this case, the sensitive information is a session token. If the attacker gets this session token it can hijack the victim session and authenticate in the application as if was the victim, accessing is account.

# Generic How-to fix

Applications should replace the usage of session tokens in the URL by session cookies, which is the recommended method to transmit session tokens in HTTP requests. 

The application should set a cookie using the adequate programming language function, which will result in an HTTP response with something similar to `Set-Cookie: sessionid=cppynyovhdltchrlezxusy44; HttpOnly; Secure`.



