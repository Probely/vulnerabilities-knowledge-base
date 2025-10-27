---
name: Spring4Shell
severity: critical
cvss-score: 10.0
cvss-vector: CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:C/C:H/I:H/A:H
cwe-id: CWE-94
cwe-name: Improper Control of Generation of Code ('Code Injection')
compliance:
  HIPAA: 164.306(a)
  ISO 27001: A.5.33, A.5.34, A.8.3, A.8.9, A.8.12
  PCI-DSS v4.0.1: 6.2.4

---            

A remote code execution vulnerability (RCE) allows the attacker to execute arbitrary code and operating system commands on the server. In the worst-case scenario, the attacker will be able to fully compromise the server, extract sensitive data, modify the application contents or delete data.

The Spring4Shell RCE vulnerability (CVE-2022-22965) can be easily exploited if the target is running the vulnerable version of the application using Tomcat as a WAR deployment.

## How to fix

{% tabs spring4shell %}
{% tab spring4shell generic %}
To fix the Spring4Shell vulnerability, you need to update all instances of the Spring Framework to version 5.3.18 and 5.2.20, or above, and the Spring Boot (depends on the Spring Framework) to version 2.5.12 and 2.6.6, or above.

Please bear in mind that one of the payloads required to identify this vulnerability might cause the web server logs to become unavailable. Restarting the server fixes this problem.
{% endtab %}

{% endtabs %}
