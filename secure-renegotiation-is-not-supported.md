
# Name

Secure Renegotiation is not supported

# Severity

Low

# CVSS Score

7.4

# CVSS Vector

CVSS:3.0/AV:N/AC:H/PR:N/UI:N/S:U/C:H/I:H/A:N

# CWE ID

CWE-264

# CWE NAME 

Permissions, Privileges, and Access Controls

# Affected Compliance

OWASP Top 10: A3

PCI-DSS: 4.1, 6.5.4

# Description

This SSL/TLS implementation does not appear to handle renegotiation handshakes properly. This may allow an attacker to insert malicious data into the HTTPS connection. A malicious renegotiation allows clients and servers to modify the encryption parameters of an existing connection, for instance to require a weaker authentication mechanism.

To successfully exploit this vulnerability, the attacker must be able to perform a man-in-the-middle attack, which typically means the attacker is physically close to either the target server or the target victim. This situation is more likely to occur in wireless connections.

The CVE for this type of vulnerability is CVE-2009-3555.

# Generic How-to fix

You can fix this problem by disabling support for the insecure renegotiation or by enabling support only for secure renegotiation. Secure renegotiation implements a different handshake for the renegotiation, making it unfeasible for the attacker to trigger the attack without being detected by either the client or the server.
