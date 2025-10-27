---
name: Expired TLS certificate
severity: medium
cvss-score: 5.3
cvss-vector: CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:N/I:L/A:N
cwe-id: CWE-324
cwe-name: Use of a Key Past its Expiration Date
compliance:
  HIPAA: 164.306(a), 164.312(c)(1), 164.312(e)(1)
  ISO 27001: A.5.14, A.8.9, A.8.24
  owasp10: A2
  pci: 4.1, 6.5.4
  PCI-DSS v4.0.1: 4.2.1, 6.2.4

---            

The TLS certificate sent by the application has expired. Web browsers will consider it invalid, and will show an error to users of your application. In most cases, browsers and TLS libraries will not allow the user to ignore the error, effectively blocking access to your application.

Using an invalid certificate will increase the user's chances of being victim to a Man-in-the-Middle attack, since this enables a malicious third party to perform the attack with any invalid certificate. This happens because it can be difficult for a user to distinguish between:

 * An expired, but legitimate, certificate sent from the server (OK)
 * An invalid certificate, sent from the attacker (not OK)

This greatly increases the likelihood of a successful MITM attack.

## How to fix

{% tabs expired-tls-certificate %}
{% tab expired-tls-certificate generic %}
To fix this issue you should install a new certificate, with an expiration date in the future. You can confirm the validity of the certificate by looking at the Not Before and Not After fields.
{% endtab %}

{% endtabs %}
