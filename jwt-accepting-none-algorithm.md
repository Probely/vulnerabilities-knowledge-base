---
name: JWT accepting none algorithm
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

`none` is accepted as a valid JWT verification algorithm in your tokens. With JWT algorithm `none` there will be no integrity validation in the server. If the JWT is used to control access to the application, an attacker could take advantage of this vulnerability to forge a token and impersonate other users or even elevate privileges.

## How to fix

{% tabs jwt-accepting-none-algorithm %}
{% tab jwt-accepting-none-algorithm generic %}
The `none` can be set as the JWT verifying algorithm but, as the name describes it, it means no verification is actually performed on the JWT integrity. If the JWT is used to control access to the application, an attacker could take advantage of this vulnerability to forge a token and impersonate other users or even elevate privileges.
{% endtab %}

{% endtabs %}
