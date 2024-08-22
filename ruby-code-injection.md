---
name: Ruby code injection
severity: high
cvss-score: 7.3
cvss-vector: CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:L/I:L/A:L
cwe-id: CWE-94
cwe-name: Improper Control of Generation of Code ('Code Injection')
compliance:
  HIPAA: 164.306(a)
  ISO 27001: A.5.33, A.5.34, A.8.3, A.8.12
  owasp10: A3
  pci: 6.5.1
  PCI v4.0: pci4-6.2.4

---            

A Ruby code injection vulnerability allows the attacker to execute arbitrary Ruby code into the application. In the worst-case scenario, the attacker will be able to fully administrate the server, which will enable him to extract sensitive data, modify the application contents or delete data.

These attacks happen when user-supplied data (forms, cookies, HTTP headers, etc.) is passed into a function that interprets it as Ruby code. This programming pattern is well known bad practice because it is hard to ensure the function inputs are free from malicious code.

## How to fix

{% tabs ruby-code-injection %}
{% tab ruby-code-injection generic %}
The best way to fix and prevent this vulnerability is to avoid functions that interpret the input as Ruby code. The function `eval` is the most commonly used for this purpose.

If you use `eval` and its input is dynamic, and it can contain user input in any way, replace it with deterministic code that does not pass the user input to that function.

It is strongly recommended not to rely on a list of accepted or rejected inputs, as those might be incomplete or have bypasses that can lead to code injection with a different payload.
{% endtab %}

{% endtabs %}
