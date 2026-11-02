---
name: Video.js library with known vulnerabilities
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

The application uses an outdated version of the Video.js library, which has known vulnerabilities.

CVE-2021-23414 affects Video.js versions before 7.14.3. The library's URL handling can allow cross-site scripting when attacker-controlled input reaches the affected code.

See the [maintainer's security fix](https://github.com/videojs/video.js/commit/b3acf663641fca0f7a966525a72845af7ec5fab2) and [official releases](https://github.com/videojs/video.js/releases).

## How to fix

{% tabs videojs-library-with-known-vulnerabilities %}
{% tab videojs-library-with-known-vulnerabilities generic %}
Upgrade Video.js to the latest maintained release containing the 7.14.3 fix and all subsequent applicable security fixes.

Update all player bundles and hosted copies. Validate untrusted URLs and review plugins that supply URLs to the player.
{% endtab %}

{% endtabs %}
