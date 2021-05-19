
# Name

Expired TLS certificate

# Severity

Medium

# CVSS Score

5.8

# CVSS Vector

CVSS:3.0/AV:N/AC:H/PR:N/UI:R/S:C/C:L/I:L/A:L

# CWE ID

CWE-324

# CWE NAME 

Use of a Key Past its Expiration Date

# Affected Compliance

OWASP Top 10: A3

PCI-DSS: 4.1, 6.5.4

# Description

The TLS certificate sent by the application has expired. Web browsers will consider it invalid, and will show an error to users of your application. In most cases, browsers and TLS libraries will not allow the user to ignore the error, effectively blocking access to your application.

Using an invalid certificate will increase the user's chances of being victim to a Man-in-the-Middle attack, since this enables a malicious third party to perform the attack with any invalid certificate. This happens because it can be difficult for a user to distinguish between:

 * An expired, but legitimate, certificate sent from the server (OK)
 * An invalid certificate, sent from the attacker (not OK)

This greatly increases the likelihood of a successful MITM attack.

# Generic How-to fix

To fix this issue you should install a new certificate, with an expiration date in the future. You can confirm the validity of the certificate by looking at the Not Before and Not After fields.
