---
name: Quill library with known vulnerabilities
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

The application uses a version of the Quill library with known vulnerabilities.

Quill 2.0.3 is affected by CVE-2025-15056: HTML export of formula and video embeds can include unescaped values. Rendering this exported HTML without sanitization can allow cross-site scripting. An older report, CVE-2021-3163, concerns versions through 1.3.7 and is disputed.

See the [CVE-2025-15056 researcher advisory](https://fluidattacks.com/advisories/diomedes) and [official release history](https://github.com/slab/quill/releases).

## How to fix

{% tabs quill-library-with-known-vulnerabilities %}
{% tab quill-library-with-known-vulnerabilities generic %}
Sanitize and correctly escape exported HTML before rendering it, including HTML produced from formula and video embeds. Restrict untrusted embed content and validate the fields used to construct it.

Check the official security guidance and release notes for a fix applicable to your version. Quill 2.0.3 is itself affected by CVE-2025-15056; upgrading to that release alone does not remediate the issue.
{% endtab %}

{% endtabs %}
