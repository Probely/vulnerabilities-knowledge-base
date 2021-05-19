
# Name

Server Cipher Order not configured

# Severity

High

# CVSS Score

7.4

# CVSS Vector

CVSS:3.0/AV:N/AC:H/PR:N/UI:N/S:U/C:H/I:H/A:N

# CWE ID

CWE-757

# CWE NAME 

Selection of Less-Secure Algorithm During Negotiation ('Algorithm Downgrade')

# Affected Compliance

OWASP Top 10: A3

PCI-DSS: 4.1, 6.5.4

# Description

The server does not define a preferred order in which the cipher suites are chosen, thus giving priority to the client's cipher suite list, which will make some clients choose the first one from the list. This is an insecure behavior since clients may not send the more secure cipher suites first, causing the SSL/TLS handshake to negotiate with weaker cipher suites that were only enabled for compatibility with older clients.

Connections negotiated with less secure cipher suites will be at risk if an attacker is able to eavesdrop the communications, something that is likely if the victim is using an wireless connection and the attacker is in its vicinity.

# Generic How-to fix

The server should set the order of the cipher suites it supports, typically with the most secure first and force that order to be honored. 
The correct configuration is server-specific but typically requires changing two settings:  the cipher suite list correctly ordered, from the most secure to the least secure, and enabling the cipher suite server order honoring.

Depending on the situation there may be a tradeoff between putting the most secure or faster cipher suites first.
