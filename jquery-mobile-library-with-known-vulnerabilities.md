---
name: JQuery Mobile library with known vulnerabilities
severity: low
cvss-score: 4.8
cvss-vector: CVSS:3.1/AV:N/AC:H/PR:N/UI:N/S:U/C:L/I:L/A:N
cwe-id: CWE-1035
cwe-name: OWASP Top Ten 2017 Category A9 - Using Components with Known Vulnerabilities
compliance:
  HIPAA: 164.306(a)
  ISO 27001: A.8.9
  owasp10: A5, A6
  pci: '6.2'
  PCI-DSS v4.0.1: 6.2.4, 6.3.3

---            

The application uses an outdated version of the JQuery Mobile library, which has known vulnerabilities.

## How to fix

{% tabs jquery-mobile-library-with-known-vulnerabilities %}
{% tab jquery-mobile-library-with-known-vulnerabilities generic %}
To fix this issue, please update JQuery Mobile to the latest available version on its official website.

Do not forget to update all the JQuery Mobile files you have on the server.
{% endtab %}

{% endtabs %}
