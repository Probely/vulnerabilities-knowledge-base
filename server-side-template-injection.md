---
name: Server-side template injection
severity: high
cvss-score: 5.3
cvss-vector: CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:L/I:N/A:N
cwe-id: CWE-94
cwe-name: Improper Control of Generation of Code ('Code Injection')
compliance:
  HIPAA: 164.306(a)
  ISO 27001: A.5.33, A.5.34, A.8.3, A.8.12
  owasp10: A3
  pci: 6.5.1
  PCI v4.0: pci4-6.2.4

---            

A server-side template injection vulnerability occurs when user input is placed in a server-side template. An attacker may be able to inject template directives with the objective of executing arbitrary code.
The impact of this vulnerability depends on various factors, such as the template engine and what characters can be used in the payload. The most straightforward attacks give the attacker the ability to read information that it should not have access to. In some cases, this type of vulnerability may give the attacker full control over the server.

## How to fix

{% tabs server-side-template-injection %}
{% tab server-side-template-injection generic %}
The best recommendation is to avoid having templates depending on user input. Try to restrict any user input to template parameters and follow the template engine documentation on how to prevent injection vulnerabilities.
{% endtab %}

{% endtabs %}
