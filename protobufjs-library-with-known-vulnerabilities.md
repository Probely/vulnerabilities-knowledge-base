---
name: protobuf.js library with known vulnerabilities
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

The application uses an outdated version of the protobuf.js library, which has known vulnerabilities.

Known issues include:

- Regular expression denial of service (CVE-2018-3738) in versions before 5.0.3, or from 6.0.0 before 6.8.6.
- Prototype pollution (CVE-2022-25878) in versions from 6.10.0 before 6.10.3, or from 6.11.0 before 6.11.3.
- Prototype pollution (CVE-2023-36665) in versions from 6.10.0 before 6.11.4, or from 7.0.0 before 7.2.5.

The impact depends on the affected version and how the application processes untrusted input.

See the [maintainer's security advisories](https://github.com/protobufjs/protobuf.js/security/advisories) and [RetireJS advisory references](https://github.com/RetireJS/retire.js/blob/master/repository/jsrepository-master.json).

## How to fix

{% tabs protobufjs-library-with-known-vulnerabilities %}
{% tab protobufjs-library-with-known-vulnerabilities generic %}
Upgrade protobuf.js to a maintained release containing all applicable security fixes, and update dependencies that bundle it. The historical 6.11.4 and 7.2.5 fixes do not cover all later advisories.

Update every deployed browser bundle and server dependency. Avoid accepting untrusted schema definitions or configuration unless the application explicitly validates them.
{% endtab %}

{% endtabs %}
