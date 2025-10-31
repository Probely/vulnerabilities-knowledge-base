---
name: WordPress version with known vulnerabilities
severity: high
cvss-score: 7.3
cvss-vector: CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:L/I:L/A:L
cwe-id: CWE-1035
cwe-name: OWASP Top Ten 2017 Category A9 - Using Components with Known Vulnerabilities
compliance:
  HIPAA: 164.306(a)
  ISO 27001: A.8.9
  owasp10: A5, A6
  pci: '6.2'
  PCI-DSS v4.0.1: 6.2.4, 6.3.3

---            

The installed version of WordPress has multiple known vulnerabilities that may be used by attackers to harmful the clients of the application or the application itself.

The impact of this greatly depends on the vulnerabilities this WordPress version has. Some vulnerabilities may allow only the theft of a user account, giving the attacker the possibility to read and modify content written by the victim and to post on is behalf.
However, more serious vulnerabilities may allow the attacker to login with the administrator account and completely control the administration area, possibly destroy all the contents or replacing them with improper content.

This is a common problem amongst WordPress installations, since it becomes outdated quickly, with vulnerabilities being discovered weekly and updated being published at the same pace.

## How to fix

{% tabs wordpress-version-with-known-vulnerabilities %}
{% tab wordpress-version-with-known-vulnerabilities generic %}
The correct solution is to update WordPress to its latest stable version, which will fix any known vulnerability, improving the security of the web application.

The easiest method to install the latest version is through the WordPress update feature:
1. go to the `/wp-admin/update-core.php` page on your application. 
1. an indication of an update should appear: `An updated version of WordPress is available.` If it doesn't appear, press `Check Again`.
1. press `Update Now` and follow the instructions. This should only take a few minutes.
1. you should also update any plugin or theme you have installed, since these are often a source of vulnerabilities. To this press `Update Plugins` and afterwards `Update Themes`.


If you cannot update through the site (for instance, if the update process fails), you will have to do it manually. The manual update process is described at the WordPress site, at `https://codex.wordpress.org/Updating_WordPress#Manual_Update`.
{% endtab %}

{% endtabs %}
