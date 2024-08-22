---
name: Insecure browser XSS protection enabled
severity: low
cvss-score: 4.7
cvss-vector: CVSS:3.0/AV:N/AC:H/PR:N/UI:R/S:C/C:L/I:L/A:N
cwe-id: CWE-16
cwe-name: Configuration
compliance:
  HIPAA: 164.306(a)
  ISO 27001: A.8.9
  owasp10: A5
  PCI v4.0: pci4-6.2.4

---            

The application explicitly enables the browser Cross-Site Scripting (XSS) Auditor functionality in an insecure mode, which might reduce the level of protection browsers provide to users.
The Auditor detects and blocks the execution of malicious code that may be present in a URL, reducing the chances of an attacker being able to explore an XSS vulnerability in the application.

However, with the current configuration, the Auditor might be abused to disable benign JavaScript on the page selectively. Consider the following example, where the target has a script tag like the following, which does some security functions:

`<script src="/security.min.js"></script> `

When the Auditor is looking for possible XSS attacks, it will check query string parameters reflected on the page. If the attacker sends the victim the following URL

`example.com/?foo=<script src="/security.min.js"></script>`

the Auditor will consider it an XSS attack because the query string parameter matches the content on the page. With the current header value, the Auditor will filter the script tag, remove it from the page, and load the remainder as usual, turning off any protections offered by the security.js script. This might be dangerous as it allows an attacker to selectively disable JS on the vulnerable page.

## How to fix

{% tabs insecure-browser-xss-protection-enabled %}
{% tab insecure-browser-xss-protection-enabled generic %}
This problem is caused because the application sends the header **X-XSS-Protection** with value **1**, so you can either stop sending the header or change it to **0**, or **1; mode=block**.

By default, modern browsers have the XSS protection disabled. Therefore, not sending the header at all will keep the XSS filter disabled.
Since this feature is deprecated and no longer supported in modern browsers, we recommend not sending the header at all.
{% endtab %}

{% endtabs %}
