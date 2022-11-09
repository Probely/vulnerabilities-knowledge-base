---
name: PHP code injection
severity: high
cvss-score: 8.6
cvss-vector: CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:L/A:L
cwe-id: CWE-94
cwe-name: Improper Control of Generation of Code ('Code Injection')
compliance:
  owasp10: A3
  pci: 6.5.1

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
