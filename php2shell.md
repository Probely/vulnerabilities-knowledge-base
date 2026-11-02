---
name: PHP2Shell
severity: critical
cvss-score: 9.8
cvss-vector: CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H
cwe-id: CWE-416
cwe-name: Use After Free
compliance: {}
---

PHP2Shell refers to CVE-2026-109618 and CVE-2026-109619, memory-safety vulnerabilities in PHP request processing. An unauthenticated attacker may be able to read server memory or execute arbitrary code, depending on the affected version, configuration, and execution environment.

The supported PHP branches received fixes in versions 8.2.35, 8.3.36, 8.4.27, and 8.5.12. Earlier releases in those branches are affected; unsupported branches require a maintained vendor patch or migration to a supported release.

See the PHP maintainers' [out-of-memory handling advisory](https://github.com/php/php-src/security/advisories/GHSA-w8hw-w9fx-j79w) and [stale-state advisory](https://github.com/php/php-src/security/advisories/GHSA-6wmf-4rv5-p3rp). The CVSS 3.1 score above is the scanner's rating; the upstream advisories separately publish CVSS 4.0 scores of 9.2.

## How to fix

{% tabs php2shell %}
{% tab php2shell generic %}
Upgrade to the latest supported PHP security release for your branch, including at least the 8.2.35, 8.3.36, 8.4.27, or 8.5.12 fixes as applicable. For distribution-provided PHP, verify the vendor's advisory and patched package version because fixes may be backported.

Restart PHP workers and application services so every running process uses the patched runtime. Check all affected containers and hosts. Configuration mitigations are incomplete and should not replace patching.
{% endtab %}

{% endtabs %}
