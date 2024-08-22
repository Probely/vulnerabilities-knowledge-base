---
name: Cookie with SameSite attribute set to None
severity: low
cvss-score: 3.1
cvss-vector: CVSS:3.0/AV:N/AC:H/PR:N/UI:R/S:U/C:L/I:N/A:N
cwe-id: CWE-1275
cwe-name: Sensitive Cookie with Improper SameSite Attribute
compliance:
  HIPAA: 164.306(a), 164.312(c)(1), 164.312(e)(1)
  ISO 27001: A.5.14, A.8.9, A.8.24
  owasp10: A2, A7
  pci: 4.1, 6.5.4, 6.5.10
  PCI v4.0: pci4-4.2.1, pci4-6.2.4

---            

We found a Set-Cookie header with the SameSite cookie attribute set to None. Although this is not a vulnerability by itself, the SameSite cookie attribute defines whether cookies are sent in cross-site requests. If properly configured, SameSite makes Cross-Site Request Forgery (CSRF) attacks impossible or very hard to perpetrate. If set to None, this protection is not enabled.

## How to fix

{% tabs cookie-with-samesite-attribute-set-to-none %}
{% tab cookie-with-samesite-attribute-set-to-none generic %}
Set the SameSite cookie attribute to `strict` to mitigate CSRF attacks. If `strict` breaks any functionality, use `lax` instead, which gives you protection against POST-based CSRF, but not GET ones.
{% endtab %}

{% endtabs %}
