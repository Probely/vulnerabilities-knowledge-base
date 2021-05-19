
# Name

TLS certificate about to expire

# Severity

Low

# CVSS Score



# CVSS Vector

CVSS:3.0/AV:N/AC:H/PR:N/UI:R/S:C/C:N/I:N/A:N

# CWE ID

CWE-324

# CWE NAME 

Use of a Key Past its Expiration Date

# Affected Compliance

OWASP Top 10: A3

# Description

The TLS certificate sent by the application will expire soon. Web browsers will consider it invalid and will show an error to users of your application. In most cases, browsers and TLS libraries will not allow users to ignore the error, effectively blocking access to your application.

Using an invalid certificate will increase the user's chances of being victim to a Man-in-the-Middle attack, since this enables a malicious third party to perform the attack with any invalid certificate. This happens because it can be difficult for a user to distinguish between:

 * An expired, but legitimate, certificate sent from the server (OK)
 * An invalid certificate, sent from the attacker (not OK)

This greatly increases the likelihood of a successful MITM attack.

# Generic How-to fix

In order to fix this issue, you should renew the certificate and deploy it in your server before the expiration date of the current certificate. 

You can confirm the expiration date of the certificate by looking at the ```Not After``` field.
