---
name: Server-side request forgery
severity: high
cvss-score: 4.8
cvss-vector: CVSS:3.1/AV:N/AC:H/PR:N/UI:N/S:U/C:N/I:L/A:L
cwe-id: CWE-918
cwe-name: Server-Side Request Forgery (SSRF)
compliance:
  HIPAA: 164.306(a)
  ISO 27001: A.5.33, A.5.34, A.8.3, A.8.4, A.8.12
  owasp10: A10
  pci: 6.5.1
  PCI v4.0: pci4-6.2.4

---            

In a Server-side request forgery (SSRF) attack, the attacker tricks the vulnerable application into sending a custom request to an internal application. The attacker might be able to exfiltrate information by making requests to internal applications that otherwise would be out of reach from the attacker. This attack can also be used to trigger actions on those applications, bypassing the restriction of only being available internally.

## How to fix

{% tabs server-side-request-forgery %}
{% tab server-side-request-forgery generic %}
The best strategy is to have a filter on the identified vulnerable parameter with a whitelist of URLs where the server can execute requests to. Alternatively, the filter can have patterns for allowed URLs. In case you already have filters in place, review and refine them to be more effective.
{% endtab %}

{% endtabs %}
