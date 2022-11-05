---
name: Application error message
severity: medium
cvss-score: 5.3
cvss-vector: CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:L/I:N/A:N
cwe-id: CWE-550
cwe-name: Server-generated Error Message Containing Sensitive Information
compliance:
  owasp10: A5
  pci: 6.5.5

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
