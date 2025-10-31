---
name: PHP code injection
severity: critical
cvss-score: 9.8
cvss-vector: CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H
cwe-id: CWE-94
cwe-name: Improper Control of Generation of Code ('Code Injection')
compliance:
  HIPAA: 164.306(a)
  ISO 27001: A.5.33, A.5.34, A.8.3, A.8.12, A.8.25
  owasp10: A3
  pci: 6.5.1
  PCI-DSS v4.0.1: 6.2.4

---            

A PHP code injection vulnerability allows the attacker to execute arbitrary PHP code into the application. In the worst-case scenario, the attacker will be able to fully administrate the server, which will enable him to extract sensitive data, modify the application contents or delete data.

These attacks happen when user-supplied data (forms, cookies, HTTP headers, etc.) is passed into a function that interprets it as PHP code. This programming pattern is well known bad practice because it is hard to ensure the function inputs are free from malicious code.

## How to fix

{% tabs php-code-injection %}
{% tab php-code-injection generic %}
The best way to fix and prevent this vulnerability is to avoid functions that interpret the input as PHP code. The functions `eval` and `include` are the most commonly used for this purpose.

If you use those functions and its input is dynamic, and it can contain user input in any way, replace them with deterministic code that does not pass the user input to those functions.

It is strongly recommended not to rely on a list of accepted or rejected inputs, as those might be incomplete or have bypasses that can lead to code injection with a different payload.
{% endtab %}

{% endtabs %}
