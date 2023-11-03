---
name: Joomla! version with known vulnerabilities
severity: high
cvss-score: 9.1
cvss-vector: CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:N
cwe-id: CWE-1035
cwe-name: OWASP Top Ten 2017 Category A9 - Using Components with Known Vulnerabilities
compliance:
  ISO 27001: A.8.9
  owasp10: A5, A6
  pci: '6.2'

---            

The installed version of Joomla has multiple known vulnerabilities that may be used by attackers to harmful the clients of the application or the application itself.

The impact of this greatly depends on the vulnerabilities this Joomla version has. Some vulnerabilities may allow only the theft of a user account, giving the attacker the possibility to read and modify content written by the victim and to post on is behalf.
However, more serious vulnerabilities may allow the attacker to login with the administrator account and completely control the administration area, possibly destroy all the contents or replacing them with improper content.

This is a common problem amongst Joomla installations, since it becomes outdated quickly, with vulnerabilities being discovered weekly and updated being published at the same pace.

## How to fix

{% tabs joomla-version-with-known-vulnerabilities %}
{% tab joomla-version-with-known-vulnerabilities generic %}
The correct solution is to update Joomla to its latest stable version, which will fix any known vulnerability, improving the security of the web application.
{% endtab %}

{% endtabs %}
