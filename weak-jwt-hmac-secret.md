---
name: Weak JWT HMAC secret
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

The secret used to create the JWT signature can be guessed easily. If the JWT is used to control access to the application, an attacker could take advantage of this vulnerability to forge a token and impersonate other users or even elevate privileges.

## How to fix

{% tabs weak-jwt-hmac-secret %}
{% tab weak-jwt-hmac-secret generic %}
To fix this issue, you must use a secret that cannot be guessed. For instance, if you use `hs256` as a signing algorithm, ensure its key has at least 256 bits. To generate a key with the desired length, use a cryptographically secure random generator function to generate a 32 bytes string (256 bits).
{% endtab %}

{% endtabs %}
