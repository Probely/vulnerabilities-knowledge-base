---
name: Marked library with known vulnerabilities
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

The application uses an outdated version of the Marked library, which has known vulnerabilities.

Known issues include regular expression denial of service (CVE-2022-21680 and CVE-2022-21681) in versions before 4.0.10. Processing specially crafted Markdown with an affected version can consume excessive CPU resources.

See the maintainer's [CVE-2022-21680 advisory](https://github.com/markedjs/marked/security/advisories/GHSA-rrrm-qjm4-v8hf), [CVE-2022-21681 advisory](https://github.com/markedjs/marked/security/advisories/GHSA-5v2h-r2cx-5xgj), and [current security advisories](https://github.com/markedjs/marked/security/advisories).

## How to fix

{% tabs marked-library-with-known-vulnerabilities %}
{% tab marked-library-with-known-vulnerabilities generic %}
Upgrade Marked to the latest maintained release containing all applicable security fixes. Version 4.0.10 fixes the two historical issues above, but it is not a sufficient minimum for all later advisories.

Update every deployed copy. Sanitize generated HTML before rendering untrusted Markdown; upgrading the parser does not replace output sanitization.
{% endtab %}

{% endtabs %}
