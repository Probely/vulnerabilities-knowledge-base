---
name: Missing redirect to HTTPS
severity: low
cvss-score: 7.4
cvss-vector: CVSS:3.0/AV:N/AC:H/PR:N/UI:N/S:U/C:H/I:H/A:N
cwe-id: CWE-319
cwe-name: Cleartext Transmission of Sensitive Information
compliance: {}

---            

The application does not redirect clients from HTTP to HTTPS. Thus, if a client visits the application through HTTP, it will not be redirected to HTTPS and will continue browsing over an unencrypted and insecure connection.
An attacker that is strategically positioned between the victim's and the applications's traffic is able to eavesdrop all communications between them, accessing any information that is being transmitted, such as the victim's credentials. In addition, the attacker can modify the communications to deliver more powerful attacks, for instance, to ask the victim for more sensitive information that hasn't been asked in the original application page.

Such attacks are more likely to occur when the victim is using an insecure Wi-Fi connection, a typical scenario in the public Wi-Fi services.

Unencrypted connections may also trigger browser warnings about the insecurity of the connection, following the trend of raising awareness about privacy.

## How to fix

{% tabs missing-redirect-to-https %}
{% tab missing-redirect-to-https generic %}
The application should be configured to use encryption in all communications. This means to configure the web server to force all incoming requests in plaintext (unencrypted) to be redirected to the HTTPS version of the application.

In HTTP this is achieved with a `301 Moved Permanently` directive. It can be complemented with an HTTP Strict Transport Security header (HSTS) to force the browsers to make all requests in HTTPS even if the end user forgets to write HTTPS in the request.
{% endtab %}

{% endtabs %}
