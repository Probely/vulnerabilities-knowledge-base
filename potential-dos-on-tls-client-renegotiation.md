
# Name

Potential DoS on TLS Client Renegotiation

# Severity

Low

# CVSS Score

5.3

# CVSS Vector

CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:N/I:N/A:L

# CWE ID

CWE-264

# CWE NAME 

Permissions, Privileges, and Access Controls

# Affected Compliance

OWASP Top 10: A3

PCI-DSS: 4.1, 6.5.4

# Description

The server does not appear to limit the number of client-initiated renegotiation handshakes. Typically, when a client starts a new TLS connection, the server will expend more CPU resources than the client. The client may exploit this resource usage asymmetry to launch a DoS attack over a single TCP connection.

After connecting, the client may request a large number of renegotiation attempts until the server runs out of CPU. Since a malicious client may launch the attack over a single TCP connection, it could evade rate-limiting rules that may already be in-place by firewalls (e.g., maximum connections per second).

The CVE for this type of vulnerability is CVE-2011-1473.

# Generic How-to fix

You should ensure that both the server and the TLS library are updated to the most recent versions.
