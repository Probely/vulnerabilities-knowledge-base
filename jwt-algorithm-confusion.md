---
name: JWT algorithm confusion
severity: high
cvss-score: 10.0
cvss-vector: CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:C/C:H/I:H/A:H
cwe-id: CWE-345
cwe-name: Insufficient Verification of Data Authenticity
compliance:
  ISO 27001: A.8.2, A.8.3, A.8.5, A.8.24, A.8.26
  owasp10: A8

---            

The server uses public/private key signatures to protect the JWTs. But it also accepts JWTs signed with HMAC. By changing the signing algorithm in your JWTs to HMAC and using the HTTPS certificate as secret we created a JWT accepted by your server. If the JWT is used to control access to the application, an attacker could take advantage of this vulnerability to forge a token and impersonate other users or even elevate privileges.

## How to fix

{% tabs jwt-algorithm-confusion %}
{% tab jwt-algorithm-confusion generic %}
To fix this issue, you should only have public/private key algorithms in the list of allowed algorithms.
{% endtab %}

{% endtabs %}
