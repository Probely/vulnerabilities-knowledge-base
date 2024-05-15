---
name: JWT signature is not being verified
severity: high
cvss-score: 7.5
cvss-vector: CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:N/I:H/A:N
cwe-id: CWE-345
cwe-name: Insufficient Verification of Data Authenticity
compliance:
  HIPAA: 164.306(a), 164.312(c)(1)
  ISO 27001: A.8.2, A.8.3, A.8.5, A.8.24
  owasp10: A8

---            

The JWT signature is not being verified by the server. If the JWT is used to control access to the application, an attacker could take advantage of this vulnerability to forge a token and impersonate other users or even elevate privileges.

## How to fix

{% tabs jwt-signature-is-not-being-verified %}
{% tab jwt-signature-is-not-being-verified generic %}
To fix this issue, you should check the signature of the JWT before reading/using the payload content.
{% endtab %}

{% endtabs %}
