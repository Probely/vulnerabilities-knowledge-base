---
name: Log file disclosure
severity: low
cvss-score: 5.3
cvss-vector: CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:L/I:N/A:N
cwe-id: CWE-200
cwe-name: Exposure of Sensitive Information to an Unauthorized Actor
compliance:
  HIPAA: 164.306(a)
  ISO 27001: A.8.9, A.8.15
  owasp10: A5
  PCI v4.0: pci4-6.2.4

---            

A log file was found in the application document root, meaning it is available for viewing to anyone browsing through the application.

Since the location of the log file is easy to guess or it is a well-known path used for logs, it is very easy for an attacker to find it and take advantage of sensitive data that it may contain. Depending on the information present in the log, access to it may increase the probability of exploitation of other vulnerabilities, or even facilitate the take over of user accounts.

## How to fix

{% tabs log-file-disclosure %}
{% tab log-file-disclosure generic %}
To fix this problem, change the location of the log file at the application configuration. You can, and should, also prevent your web server from serving files with the extension `.log`. This will add an extra layer of protection in the case any log is left in the document root.
{% endtab %}

{% endtabs %}
