---
name: React2Shell
severity: critical
cvss-score: 10.0
cvss-vector: CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:C/C:H/I:H/A:H
cwe-id: CWE-502
cwe-name: Deserialization of Untrusted Data
compliance:
  HIPAA: "164.306(a)"
  ISO 27001: "A.5.33, A.5.34, A.8.12, A.8.3"
  owasp10: "A3"
  pci: "6.5.1"
  PCI-DSS v4.0.1: "6.2.4"
---

React2Shell (CVE-2025-55182) is an unauthenticated remote code execution vulnerability in React Server Components. Unsafe deserialization of requests to server function endpoints can allow an attacker to execute code on the server. Applications that do not use a framework or bundler supporting React Server Components are not affected by this vulnerability.

Affected packages include react-server-dom-webpack, react-server-dom-parcel, and react-server-dom-turbopack versions 19.0.0, 19.1.0, 19.1.1, and 19.2.0. Next.js tracks its downstream impact as CVE-2025-66478.

See the [React maintainer advisory](https://github.com/react/react/security/advisories/GHSA-fv66-9v8q-g76r) and [framework-specific guidance](https://vercel.com/kb/bulletin/react2shell).

## How to fix

{% tabs react2shell %}
{% tab react2shell generic %}
Upgrade the affected React Server Components packages and the framework that supplies them to maintained releases containing all applicable security fixes. React's original RCE fixes were 19.0.1, 19.1.2, and 19.2.1, but later security advisories require additional updates.

Follow the [current React security guidance](https://react.dev/blog/2025/12/11/denial-of-service-and-source-code-exposure-in-react-server-components), rebuild, and redeploy every affected application. Verify the versions actually deployed, including transitive dependencies. If the service was exposed while vulnerable, investigate possible compromise and rotate any secrets that may have been exposed.
{% endtab %}

{% endtabs %}
