---
name: Cookie with SameSite attribute set to None
severity: low
cvss-score: 3.1
cvss-vector: CVSS:3.0/AV:N/AC:H/PR:N/UI:R/S:U/C:L/I:N/A:N
cwe-id: CWE-1275
cwe-name: Sensitive Cookie with Improper SameSite Attribute
compliance: {}

---            

We found a Set-Cookie header with the SameSite cookie attribute set to None. Although this is not a vulnerability by itself, the SameSite cookie attribute defines whether cookies are sent in cross-site requests. If properly configured, SameSite makes Cross-Site Request Forgery (CSRF) attacks impossible or very hard to perpetrate. If set to None, this protection is not enabled.

## How to fix

{% tabs cookie-with-samesite-attribute-set-to-none %}
{% tab cookie-with-samesite-attribute-set-to-none generic %}
Change the SameSite cookie attribute to lax or, if possible, change it to strict.
{% endtab %}

{% endtabs %}
