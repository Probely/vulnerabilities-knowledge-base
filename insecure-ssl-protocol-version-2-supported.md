
# Name

Insecure SSL protocol version 2 supported

# Severity

Medium

# CVSS Score

7.4

# CVSS Vector

CVSS:3.0/AV:N/AC:H/PR:N/UI:N/S:U/C:H/I:H/A:N

# CWE ID

CWE-327

# CWE NAME 

Use of a Broken or Risky Cryptographic Algorithm

# Affected Compliance

OWASP Top 10: A3

PCI-DSS: 4.1, 6.5.4

# Description

SSL protocol version 2 is outdated and insecure. This version has multiple design flaws that may allow an attacker to eavesdrop on SSL-enabled communications.

SSL version 2 is particularly insecure since multiple practical vulnerabilities have been shown, making it easy to intercept any communication where SSL version 2 is used.

In any case, the attacker needs to be positioned between any endpoint participating in the connection, so it can eavesdrop and intercept the communications. This is fairly common, considering the frequency people connect establish connections over open Wi-Fi.

# Generic How-to fix

To fix this vulnerability, you need to disable SSL version 2, and enable TLS 1.2 and TLS 1.3, if they are not enabled already.

You should disable SSL 2, and enable TLS 1.2 and above. If you are keeping SSL and older TLS versions (i.e. TLS <= 1.1) enabled  to support "older devices", do note that as of 2018, TLS 1.2 is at 94%+ adoption. So there is a strong argument to keep only TLS 1.2 and above enabled.

You must change the web server configuration to enable or disable the protocols, so this will depend on your particular web server configuration procedures.
