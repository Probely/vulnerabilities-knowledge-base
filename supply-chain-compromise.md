---
name: Supply Chain Compromise
severity: high
cvss-score: 7.2
cvss-vector: CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:C/C:L/I:N/A:L
cwe-id: CWE-1395
cwe-name: Dependency on Vulnerable Third-Party Component
compliance:
  HIPAA: 164.306(a)
  ISO 27001: A.8.9
  owasp10: A5, A6
  pci: '6.2'
  PCI-DSS v4.0.1: 6.2.4, 6.3.3

---            

This type of vulnerability occurs when the application uses a third-party component (such as a library or module) that is compromised, affecting the application and its users.
For example, suppose the application includes a JavaScript library from an external domain. If a malicious actor can compromise that library, all applications loading it will run the malicious code. 

The impact will depend mostly on the changes performed to the compromised third-party component, which can range from redirecting the user to a replica of the application as part of a phishing campaign to directly delivering malware to visitors.

## How to fix

{% tabs supply-chain-compromise %}
{% tab supply-chain-compromise generic %}
Fixing this vulnerability is highly dependent on the type of component. 

In some cases, there is a more recent version available, and the solution is to update the component to that version, ensuring that it fixes the problem. As an alternative, downgrading the version might also work, although it might bring back other vulnerabilities and bugs, or cause a loss of functionality.

In other scenarios, you may need to temporarily or permanently replace the component, loading it from a different domain or using a different library.
{% endtab %}

{% endtabs %}
