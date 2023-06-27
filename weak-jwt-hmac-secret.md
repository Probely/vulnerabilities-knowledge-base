---
name: Weak JWT HMAC secret
severity: high
cvss-score: 10.0
cvss-vector: CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:C/C:H/I:H/A:H
cwe-id: CWE-345
cwe-name: Insufficient Verification of Data Authenticity
compliance: {}

---            

The secret used to create the JWT signature can be guessed easily. If the JWT is used to control access to the application, an attacker could take advantage of this vulnerability to forge a token and impersonate other users or even elevate privileges.

## How to fix

{% tabs weak-jwt-hmac-secret %}
{% tab weak-jwt-hmac-secret generic %}
To fix this issue, you must use a secret that cannot be guessed. For instance, if you use `hs256` as a signing algorithm, ensure its key has at least 256 bits. To generate a key with the desired length, use a cryptographically secure random generator function to generate a 32 bytes string (256 bits).
{% endtab %}

{% endtabs %}
