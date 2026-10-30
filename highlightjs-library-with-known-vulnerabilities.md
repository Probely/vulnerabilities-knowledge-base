---
name: highlight.js library with known vulnerabilities
severity: low
cvss-score: 4.8
cvss-vector: CVSS:3.1/AV:N/AC:H/PR:N/UI:N/S:U/C:L/I:L/A:N
cwe-id: CWE-1395
cwe-name: Dependency on Vulnerable Third-Party Component
compliance:
  HIPAA: "164.306(a)"
  ISO 27001: "A.8.9"
  owasp10: "A5, A6"
  pci: "6.2"
  PCI-DSS v4.0.1: "6.2.4, 6.3.3"
---

The application uses an outdated version of the highlight.js library, which has known vulnerabilities.

Known issues include prototype pollution (CVE-2020-26237) in versions before 9.18.2 and in versions from 10.0.0 before 10.1.2. Regular expression denial of service also affects multiple language grammars in versions from 9.0.0 before 10.4.1 (GHSA-7wwv-vh3v-89cq).

See the maintainer's [prototype pollution advisory](https://github.com/highlightjs/highlight.js/security/advisories/GHSA-vfrc-7r7c-w9mx) and [denial-of-service advisory](https://github.com/highlightjs/highlight.js/security/advisories/GHSA-7wwv-vh3v-89cq).

## How to fix

{% tabs highlightjs-library-with-known-vulnerabilities %}
{% tab highlightjs-library-with-known-vulnerabilities generic %}
Upgrade highlight.js to the latest maintained release containing the applicable security fixes. Version 10.4.1 addresses the historical denial-of-service issue described above; review current advisories for later issues.

Update all distributed builds, language bundles, and copies served by the application.
{% endtab %}

{% endtabs %}
