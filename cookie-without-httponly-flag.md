
# Name

Cookie without HttpOnly flag

# Severity

Low

# CVSS Score

3.1

# CVSS Vector

CVSS:3.0/AV:N/AC:H/PR:N/UI:R/S:U/C:L/I:N/A:N

# CWE ID

CWE-16

# CWE NAME 

Configuration

# Affected Compliance

OWASP Top 10: A2

PCI-DSS: 6.5.10

# Description

Not having the HttpOnly flag means that the cookie can be accessed by client side scripts, such as JavaScript. This vulnerability by itself is not useful to an attacker since he has no control over client side scripts. However, if a Cross Site Scripting (XSS) vulnerability is present, he might be able to introduce a malicious script in the application, and without the HttpOnly flag, he could read the vulnerable cookie's value.

The most interesting cookie for an attacker is usually the session cookie as it allows him to steal the user's session. Other cookies might be interesting also, depending on the application and the cookie's purposes, so a good rule-of-thumb is to set HttpOnly flag to all cookies.

Mitigating this kind of vulnerability greatly reduces the impact of other possible vulnerabilities, such as XSS, which are very common in most sites.

# Generic How-to fix

To fix a vulnerability of this type, you just need to set the HttpOnly flag on the vulnerable cookie, effectively preventing it from being read by client side scripts.

Depending on the language and technologies you are using, setting the HttpOnly flag could mean to enable it or setting it to true, either on the code of the application itself or in a configuration file of the webserver or Content Management System (CMS) you are using.
