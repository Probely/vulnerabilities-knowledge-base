---
name: Server-side JavaScript injection
severity: high
cvss-score: 7.3
cvss-vector: CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:L/I:L/A:L
cwe-id: CWE-94
cwe-name: Improper Control of Generation of Code ('Code Injection')
compliance:
  ISO 27001: A.5.33, A.5.34, A.8.3, A.8.12, A.8.26
  owasp10: A3
  pci: 6.5.1

---            

A Server-side JavaScript injection vulnerability allows the attacker to run arbitrary JavaScript code on the server. Web Applications that pass user input to functions like `eval()`, `setTimeout()` and `setInterval()` are potentially vulnerable.

The impact of this vulnerability ranges from an effective denial-of-service attack to File System access on the server.

## How to fix

{% tabs server-side-javascript-injection %}
{% tab server-side-javascript-injection generic %}
To prevent a Server-side JavaScript injection vulnerability, you should validate all user input on the server-side before processing. 

You should also consider the following:
* Do not use the `eval()` function to parse user inputs. 
* If you need to parse JSON input, use a safer alternative such as `JSON.parse()`.
* Include ```"use strict";``` at the beginning of a function.
{% endtab %}

{% endtabs %}
