
# Name

SSL cookie without Secure flag

# Severity

Low

# CVSS Score

3.1

# CVSS Vector

CVSS:3.0/AV:N/AC:H/PR:N/UI:R/S:U/C:L/I:N/A:N

# CWE ID

CWE-614

# CWE NAME 

Sensitive Cookie in HTTPS Session Without 'Secure' Attribute

# Affected Compliance

OWASP Top 10: A2, A3

PCI-DSS: 6.5.10

# Description

The cookie secure flag is intended to prevent browsers from submitting the cookie in any HTTP requests that use an unencrypted connection, thus an attacker that is eavesdropping the connection will not be able to get that cookie.

A flag without the secure flag set will always be sent on every HTTP request that matches the scope of cookie, i.e. the domain for which it is set. What this means is that if your application inadvertently makes an HTTP request (without encryption), this request will carry the cookie and any attacker that can eavesdrop the victim traffic will be able to read that cookie.

If the cookie in question is the session cookie, the attacker will be able to hijack the victim account.

# Generic How-to fix

To fix a vulnerability of this type, you just need to set the Secure flag on the vulnerable cookie, effectively preventing it from being transmitted in unencrypted connections, i.e. over HTTP.

Depending on the language and technologies you are using, setting the Secure flag could mean to enable it or setting it to true, either on the code of the application itself or in a configuration file of the webserver or Content Management System (CMS) you are using.
