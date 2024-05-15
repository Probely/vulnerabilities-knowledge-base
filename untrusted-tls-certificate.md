---
name: Untrusted TLS certificate
severity: medium
cvss-score: 5.3
cvss-vector: CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:N/I:L/A:N
cwe-id: CWE-16
cwe-name: Configuration
compliance:
  HIPAA: 164.306(a), 164.312(c)(1), 164.312(e)(1)
  ISO 27001: A.5.14, A.8.9, A.8.24
  owasp10: A2
  pci: 4.1, 6.5.4

---            

The certificate sent by the server is not trusted.

This may be due to one of the following reasons:
  * The requested hostname does not match the CN or SAN attribute of the TLS Certificate;
  * The issuer of this certificate is not trusted. This can happen if the certificate is self-signed, or the certificate issuer is not a recognized Certificate Authority;
  * The server did not send the complete certificate chain. This usually means that the server did not send a required intermediate CA certificate.

If this problem is intermittent, it might be because your site is behind a load balancer, and one of the servers is misconfigured or is sending an incorrect certificate.

## How to fix

{% tabs untrusted-tls-certificate %}
{% tab untrusted-tls-certificate generic %}
To fix this issue, you should address all of the issues identified below.
{% endtab %}

{% endtabs %}
