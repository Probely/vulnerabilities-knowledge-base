---
name: CRLF injection
severity: low
cvss-score: 3.7
cvss-vector: CVSS:3.1/AV:N/AC:H/PR:N/UI:N/S:U/C:N/I:L/A:N
cwe-id: CWE-93
cwe-name: Improper Neutralization of CRLF Sequences ('CRLF Injection')
compliance:
  HIPAA: 164.306(a)
  ISO 27001: A.5.33, A.5.34, A.8.3, A.8.12
  owasp10: A3
  pci: 6.5.1
  PCI v4.0: pci4-6.2.4

---            

A CRLF injection vulnerability allows an attacker to inject a CR (Carriage Return: ASCII 13, \r) and a LF (Line Feed: ASCII 10, \n) in user inputs, which are then inserted in the response to terminate lines and divide the header from the body in HTTP responses, in an unexpected manner.

With a CRLF injection, an attacker takes control of the response body to perpetrate the attack. For example, the CRLF might allow the attacker to do an XSS (cross-site scripting) attack by removing the CSP (content security policy) protection and injecting malicious JavaScript into the body.

## How to fix

{% tabs crlf-injection %}
{% tab crlf-injection generic %}
To prevent a CRLF injection vulnerability, you should:

 * Not insert user input in the response headers.
 * Use a library method that properly encodes header values.

If your application needs to allow user input in a header, ensure the input only contains characters from a limited list, for instance, only alpha-numeric ones.
{% endtab %}

{% endtabs %}
