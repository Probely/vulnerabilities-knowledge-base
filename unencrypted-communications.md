---
name: Unencrypted communications
severity: high
cvss-score: 6.5
cvss-vector: CVSS:3.0/AV:N/AC:H/PR:N/UI:N/S:U/C:H/I:L/A:N
cwe-id: CWE-319
cwe-name: Cleartext Transmission of Sensitive Information
compliance:
  HIPAA: 164.306(a), 164.312(c)(1), 164.312(e)(1)
  ISO 27001: A.5.14, A.8.9, A.8.24
  owasp10: A2
  pci: 4.1, 6.5.4

---            

The application allows clients to connect to it through an unencrypted connection, meaning that an attacker that is strategically positioned between the victim's and the applications's traffic is able to eavesdrop all communications between them, accessing any information that is being transmitted, such as the victim's credentials. In addition, the attacker can modify the communications to deliver more powerful attacks, for instance, to ask the victim for more sensitive information that hasn't been asked in the original application page.

Such attacks are more likely to occur when the victim is using an insecure Wi-Fi connection, a typical scenario in the public Wi-Fi services.

Unencrypted connections may also trigger browser warnings about the insecurity of the connection, following the trend of raising awareness about privacy.

## How to fix

{% tabs unencrypted-communications %}
{% tab unencrypted-communications generic %}
The application should be configured to use encryption in all communications. This normally means to configure the web server to use TLS with a suitable choice of ciphers, forcing all incoming requests in plaintext (without encryption) to be redirected to TLS endpoint of the application.

In HTTP this is achieved with a 301 Moved Permanently directive. It can be complemented with an HTTP Strict Transport Security header (HSTS) to force the browsers to make all requests in HTTPS even if the end user forgets to write HTTPS in the request.
{% endtab %}

{% endtabs %}
