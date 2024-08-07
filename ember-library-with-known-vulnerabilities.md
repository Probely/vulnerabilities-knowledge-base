---
name: Ember library with known vulnerabilities
severity: low
cvss-score: 4.8
cvss-vector: CVSS:3.0/AV:N/AC:H/PR:N/UI:N/S:U/C:L/I:L/A:N
cwe-id: CWE-1035
cwe-name: OWASP Top Ten 2017 Category A9 - Using Components with Known Vulnerabilities
compliance:
  HIPAA: 164.306(a)
  ISO 27001: A.8.9
  owasp10: A5, A6
  pci: '6.2'
  PCI v4.0: pci4-6.2.4, pci4-6.3.3

---            

The application uses an outdated version of the Ember library, which has known vulnerabilities.

## How to fix

{% tabs ember-library-with-known-vulnerabilities %}
{% tab ember-library-with-known-vulnerabilities generic %}
To fix this issue, please update Ember to the latest available version on its official website.

Do not forget to update all the Ember files you have on the server.
{% endtab %}

{% endtabs %}
