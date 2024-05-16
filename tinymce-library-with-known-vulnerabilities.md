---
name: TinyMCE library with known vulnerabilities
severity: low
cvss-score: 4.8
cvss-vector: CVSS:3.0/AV:N/AC:H/PR:N/UI:N/S:U/C:L/I:L/A:N
cwe-id: CWE-1035
cwe-name: OWASP Top Ten 2017 Category A9 - Using Components with Known Vulnerabilities
compliance:
  HIPAA: 164.306(a)
  ISO 27001: A.8.9
  owasp10: A5
  pci: '6.2'

---            

The application uses an outdated version of the TinyMCE library, which has known vulnerabilities.

## How to fix

{% tabs tinymce-library-with-known-vulnerabilities %}
{% tab tinymce-library-with-known-vulnerabilities generic %}
To fix this issue, please update TinyMCE to the latest available version on its official website.

Do not forget to update all the TinyMCE files you have on the server.
{% endtab %}

{% endtabs %}
