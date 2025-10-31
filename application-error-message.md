---
name: Application error message
severity: medium
cvss-score: 5.3
cvss-vector: CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:L/I:N/A:N
cwe-id: CWE-550
cwe-name: Server-generated Error Message Containing Sensitive Information
compliance:
  HIPAA: 164.306(a)
  ISO 27001: A.5.33, A.5.34, A.8.4, A.8.9, A.8.12, A.8.25
  owasp10: A5
  pci: 6.5.5
  PCI-DSS v4.0.1: 6.2.4

---            

The application displays detailed technical information when errors occur, disclosing internal information such as file system paths, application stacktraces and even snippets of code. This information reveals implementation details that provide the attacker with importante cues to find more vulnerabilities.
These errors also help the attacker exploring other vulnerabilities with a much higher probability of success.

## How to fix

{% tabs application-error-message %}
{% tab application-error-message generic %}
Errors should be handled properly in the application, without being echoed to the client. Careful programming can handle most errors in a way they are catched and reported to logs but not to the client. If errors need to be displayed to the client, they should be masked and displayed with friendly texts without any internal information.

Depending on the technology used in the application, this can be configured at the framework level by enabling or disabling a setting, normally related to the displaying of errors. 
{% endtab %}

{% endtabs %}
