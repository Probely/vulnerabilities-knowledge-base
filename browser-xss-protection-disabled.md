---
name: Browser XSS protection disabled
severity: low
cvss-score: 4.7
cvss-vector: CVSS:3.0/AV:N/AC:H/PR:N/UI:R/S:C/C:L/I:L/A:N
cwe-id: CWE-16
cwe-name: Configuration
compliance:
  owasp10: A5

---            

The application explicitly disables the browser Cross-Site Scripting (XSS) filter functionality, thus reducing the level of protection browsers provide to users.
The XSS filter detects and blocks the execution of malicious code that may be present in an URL, reducing the chances of an attacker being able to explore a XSS vulnerability in the application.

This filter should be seen as an extra layer of defense against XSS, and not as replacement of the recommended XSS prevention techniques.

## How to fix

{% tabs browser-xss-protection-disabled %}
{% tab browser-xss-protection-disabled generic %}
This problem is caused because the application sends the header **X-XSS-Protection** with value **0**, so can either stop sending the header or changing it to **1**.

By default, browsers have the XSS protection enabled, therefore not sending the header at all will keep the XSS filter enabled.
Sending the header with **1** will enable the protection, if not already. The header will look like this:

	X-XSS-Protection: 1

Additionally there is one optional directive for this header: **mode=block**.   

	X-XSS-Protection: 1; mode=block

This directive instructs the browser to stop rendering the page if a malicious payload is detected in URL, instead of sanitizing the URL by removing the malicious parts, which is the default behavior. Blocking rendering is safer, since it prevents side effects caused by sanitization.
{% endtab %}

{% tab browser-xss-protection-disabled nginx %}
This problem is caused because the application sends the header **X-XSS-Protection** with value **0**, so can either stop sending the header or changing it to **1**.

By default, browsers have the XSS protection enabled, therefore not sending the header at all will keep the XSS filter enabled.
Sending the header with **1** will enable the protection, if not already. For nginx add the following line to your virtual host configuration file:

	add_header X-XSS-Protection "1" always;

Additionally there is one optional directive for this header: **mode=block**.   

	add_header X-XSS-Protection "1; mode=block" always;

This directive instructs the browser to stop rendering the page if a malicious payload is detected in URL, instead of sanitizing the URL by removing the malicious parts, which is the default behavior. Blocking rendering is safer, since it prevents side effects caused by sanitization.
{% endtab %}

{% tab browser-xss-protection-disabled apache %}
This problem is caused because the application sends the header **X-XSS-Protection** with value **0**, so can either stop sending the header or changing it to **1**.

By default, browsers have the XSS protection enabled, therefore not sending the header at all will keep the XSS filter enabled.
Sending the header with **1** will enable the protection, if not already. For Apache add the following line to your virtual host configuration file:

	Header always set X-XSS-Protection "1"

Additionally there is one optional directive for this header: **mode=block**.   

	Header always set X-XSS-Protection "1; mode=block"

This directive instructs the browser to stop rendering the page if a malicious payload is detected in URL, instead of sanitizing the URL by removing the malicious parts, which is the default behavior. Blocking rendering is safer, since it prevents side effects caused by sanitization.
{% endtab %}

{% endtabs %}
