---
name: WordPress plugin with known vulnerabilities
severity: high
cvss-score: 9.1
cvss-vector: CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:N
cwe-id: CWE-1035
cwe-name: OWASP Top Ten 2017 Category A9 - Using Components with Known Vulnerabilities
compliance:
  owasp10: A5, A6
  pci: '6.2'

---            

The Wordpress application has plugins with multiple known vulnerabilities that may be used by attackers to harmful the clients of the application or the application itself.

The impact of this greatly depends on the vulnerabilities the plugins have. Some vulnerabilities may allow only the theft of a user account, giving the attacker the possibility to read and modify content written by the victim and to post on is behalf.
However, more serious vulnerabilities may allow the attacker to login with the administrator account and completely control the administration area, possibly destroy all the contents or replacing them with improper content.

This is a common problem amongst WordPress plugins, since they become outdated quickly, with vulnerabilities being discovered weekly and updated being published at the same pace. It is also frequent for plugins to be no longer maintained, leaving users without updates that fix published vulnerabilities.

## How to fix

{% tabs wordpress-plugin-with-known-vulnerabilities %}
{% tab wordpress-plugin-with-known-vulnerabilities generic %}
The correct solution is to update all plugins to their latest stable version, which will fix any known vulnerability, improving the security of the web application.

The easiest method to install the latest version is through the plugin update feature:
1. go to the `/wp-admin/update-core.php` page on your application. 
1. an indication of an update should appear after Plugins: `The following plugins have new versions available` If it doesn't appear, press `Check Again`.
1. select all plugins and press `Update Plugins`. Some extra instructions may appear, which you should follow.
1. you should also update any theme you have installed, since these are often a source of vulnerabilities. To this press `Update Themes`.


If you cannot update through the site (for instance, if the update process fails), you will have to do it manually. The manual update process is described at each plugin page. Look in the details of each plugin for its page.
{% endtab %}

{% endtabs %}
