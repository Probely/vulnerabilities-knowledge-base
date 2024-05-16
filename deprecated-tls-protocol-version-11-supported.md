---
name: Deprecated TLS protocol version 1.1 supported
severity: low
cvss-score: 4.2
cvss-vector: CVSS:3.0/AV:A/AC:H/PR:N/UI:N/S:U/C:L/I:L/A:N
cwe-id: CWE-327
cwe-name: Use of a Broken or Risky Cryptographic Algorithm
compliance:
  HIPAA: 164.306(a), 164.312(c)(1), 164.312(e)(1)
  ISO 27001: A.5.14, A.8.9, A.8.24
  owasp10: A2
  pci: 4.1, 6.5.4

---            

TLS protocol version 1.1 is outdated and deprecated by security standards such as NIST, PCI-DSS, and alike.

This version has various design flaws that can undermine the security of your communications. The attacker still needs to be able to eavesdrop and intercept the connection before being able to deliver the attack, but given the widespread availability of open Wi-Fi hotspots, the risk cannot be ignored.

If you'd like to know more about secure TLS deployments, we have written an extensive article about it [here](https://blog.probely.com/how-to-deploy-modern-tls-in-2018-1b9a9cafc454).

## How to fix

{% tabs deprecated-tls-protocol-version-11-supported %}
{% tab deprecated-tls-protocol-version-11-supported generic %}
To fix this issue, you need to disable TLS 1.1. We also recommend that higher TLS protocol versions are enabled, ideally version 1.2 and above.

For most systems, enabling or disabling TLS versions requires a change on the web server configuration file. Therefore, refer to your web server documentation on how to do that.

If you are using Nginx, you may use the following snippet as a guideline:

```
server {
    listen 443 ssl;
    ...
    ssl_protocols TLSv1.2 TLSv1.3;
    ...
}
```

If using an Apache server, please refer to the following example:

```
<VirtualHost *:443>
    ...
    SSLProtocol        -all +TLSv1.2 +TLSv1.3
    ...
</VirtualHost>
```

Note that we are enabling TLS 1.2 and above, reflecting our ideal scenario.

If you need to cater to clients with very old TLS support, such as ancient mobile devices, and know what you are doing, you can keep TLS 1.1 enabled, despite the known weaknesses. These issues are not as serious as the SSL protocol weaknesses, but you should weigh the need to support older clients with the risk of exposing private data. Moreover, keep in mind that TLS 1.2 support is well over [95%](https://blog.probely.com/how-to-deploy-modern-tls-in-2018-1b9a9cafc454).
{% endtab %}

{% endtabs %}
