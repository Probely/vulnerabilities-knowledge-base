---
name: Broken Object Level Authorization
severity: critical
cvss-score: 9.1
cvss-vector: CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:N
cwe-id: CWE-639
cwe-name: Authorization Bypass Through User-Controlled Key
compliance:
  HIPAA: "164.306(a), 164.312(a)(1), 164.312(d)"
  ISO 27001: "A.8.2, A.8.3"
  owasp10: "A1"
  pci: "6.5.8"
---

Broken Object Level Authorization (BOLA) occurs when an API accepts an object identifier without checking whether the requester may access or modify that particular object. Changing an identifier can then expose or alter another user's records, even when the requester is allowed to use the endpoint.

The consequences depend on the affected operation and data. This is an authorization weakness rather than a vulnerability tied to one library version or CVE. Scan coverage depends on the selected API scan profile and the features available to the account.

See [OWASP API1:2023](https://owasp.org/API-Security/editions/2023/en/0xa1-broken-object-level-authorization/) and [CWE-639](https://cwe.mitre.org/data/definitions/639.html).

## How to fix

{% tabs broken-object-level-authorization %}
{% tab broken-object-level-authorization generic %}
Enforce server-side authorization for every operation on every requested object. Scope database lookups to the authenticated principal and tenant, and verify the requested action is permitted before returning or modifying data.

Do not rely on hidden UI controls or unpredictable identifiers as access controls. Deny access by default and test read, update, and delete operations using users with different roles, ownership, and tenant membership.
{% endtab %}

{% endtabs %}
