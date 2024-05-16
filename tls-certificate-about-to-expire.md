---
name: TLS certificate about to expire
severity: low
cvss-score: ''
cvss-vector: CVSS:3.0/AV:N/AC:H/PR:N/UI:R/S:C/C:N/I:N/A:N
cwe-id: CWE-324
cwe-name: Use of a Key Past its Expiration Date
compliance:
  HIPAA: 164.306(a)
  ISO 27001: A.8.9
  owasp10: A2

---            

The TLS certificate sent by the application will expire soon. Web browsers will consider it invalid and will show an error to users of your application. In most cases, browsers and TLS libraries will not allow users to ignore the error, effectively blocking access to your application.

Using an invalid certificate will increase the user's chances of being victim to a Man-in-the-Middle attack, since this enables a malicious third party to perform the attack with any invalid certificate. This happens because it can be difficult for a user to distinguish between:

 * An expired, but legitimate, certificate sent from the server (OK)
 * An invalid certificate, sent from the attacker (not OK)

This greatly increases the likelihood of a successful MITM attack.

## How to fix

{% tabs tls-certificate-about-to-expire %}
{% tab tls-certificate-about-to-expire generic %}
In order to fix this issue, you should renew the certificate and deploy it in your server before the expiration date of the current certificate. 

You can confirm the expiration date of the certificate by looking at the ```Not After``` field.
{% endtab %}

{% endtabs %}
