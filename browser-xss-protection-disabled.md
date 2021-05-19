
# Name

Browser XSS protection disabled

# Severity

Low

# CVSS Score

4.7

# CVSS Vector

CVSS:3.0/AV:N/AC:H/PR:N/UI:R/S:C/C:L/I:L/A:N

# CWE ID

CWE-16

# CWE NAME 

Configuration

# Affected Compliance

OWASP Top 10: A6

# Description

The application explicitly disables the browser Cross-Site Scripting (XSS) filter functionality, thus reducing the level of protection browsers provide to users.
The XSS filter detects and blocks the execution of malicious code that may be present in an URL, reducing the chances of an attacker being able to explore a XSS vulnerability in the application.

This filter should be seen as an extra layer of defense against XSS, and not as replacement of the recommended XSS prevention techniques.

# Generic How-to fix

This problem is caused because the application sends the header **X-XSS-Protection** with value **0**, so can either stop sending the header or changing it to **1**.

By default, browsers have the XSS protection enabled, therefore not sending the header at all will keep the XSS filter enabled.
Sending the header with **1** will enable the protection, if not already. The header will look like this:

	X-XSS-Protection: 1

Additionally there is one optional directive for this header: **mode=block**.   

	X-XSS-Protection: 1; mode=block

This directive instructs the browser to stop rendering the page if a malicious payload is detected in URL, instead of sanitizing the URL by removing the malicious parts, which is the default behavior. Blocking rendering is safer, since it prevents side effects caused by sanitization.
