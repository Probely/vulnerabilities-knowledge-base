---
name: MooTools library with known vulnerabilities
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

The application uses an outdated version of the MooTools library, which has known vulnerabilities.

Known issues affecting MooTools through 1.5.2 include regular expression denial of service (CVE-2021-32821) and prototype pollution through Object.merge() (CVE-2021-23432).

See the [original denial-of-service disclosure](https://securitylab.github.com/advisories/GHSL-2020-345-redos-mootools/) and [prototype pollution advisory](https://github.com/advisories/GHSA-x6hx-7gh3-3q98). These advisories do not identify a patched release.

## How to fix

{% tabs mootools-library-with-known-vulnerabilities %}
{% tab mootools-library-with-known-vulnerabilities generic %}
Replace MooTools with a maintained alternative, remove the affected functionality, or apply a reviewed patch for each applicable vulnerability. Upgrading to 1.5.2 does not fix the listed issues.

Until the dependency is replaced or patched, prevent untrusted input from reaching the affected regular-expression operations and Object.merge(). Review all bundled and separately hosted copies.
{% endtab %}

{% endtabs %}
