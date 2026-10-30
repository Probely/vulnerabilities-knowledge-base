---
name: Swiper library with known vulnerabilities
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

The application uses an outdated version of the Swiper library, which has known vulnerabilities.

Known issues include prototype pollution (CVE-2021-23370) in versions before 6.5.1. A later prototype pollution issue, CVE-2026-27212, affects versions from 6.5.1 before 12.1.2. Unsafe handling of attacker-controlled configuration can modify inherited object properties and affect application behavior.

See the [maintainer's CVE-2026-27212 advisory](https://github.com/nolimits4web/swiper/security/advisories/GHSA-hmx5-qpq5-p643).

## How to fix

{% tabs swiper-library-with-known-vulnerabilities %}
{% tab swiper-library-with-known-vulnerabilities generic %}
Upgrade Swiper to a maintained release containing the 12.1.2 fix and all subsequent applicable security fixes. Upgrading only to 6.5.1 does not address the later advisory.

Update every bundled or separately hosted copy, and avoid passing untrusted configuration objects to the library.
{% endtab %}

{% endtabs %}
