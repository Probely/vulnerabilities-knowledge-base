---
name: markdown-it library with known vulnerabilities
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

The application uses an outdated version of the markdown-it library, which has known vulnerabilities.

Known issues include regular expression denial of service (CVE-2022-21670) in versions before 12.3.2, and cross-site scripting in older releases (CVE-2015-3295 before 4.1.0 and CVE-2015-10005 before 3.0.0). Processing untrusted Markdown with an affected version can consume excessive resources or produce unsafe HTML.

See the [maintainer's CVE-2022-21670 advisory](https://github.com/markdown-it/markdown-it/security/advisories/GHSA-6vfc-qv3f-vr6c) and [current security advisories](https://github.com/markdown-it/markdown-it/security/advisories).

## How to fix

{% tabs markdown-it-library-with-known-vulnerabilities %}
{% tab markdown-it-library-with-known-vulnerabilities generic %}
Upgrade markdown-it to a maintained release that includes all applicable security fixes. Version 12.3.2 fixes CVE-2022-21670, but later advisories also affect newer releases; do not treat that historical minimum as complete remediation.

Update every deployed copy and any dependency that bundles markdown-it. Keep raw HTML disabled for untrusted input, or sanitize rendered HTML before inserting it into a page.
{% endtab %}

{% endtabs %}
