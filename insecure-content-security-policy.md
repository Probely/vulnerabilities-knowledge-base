---
name: Insecure Content Security Policy
severity: low
cvss-score: 3.7
cvss-vector: CVSS:3.0/AV:N/AC:H/PR:N/UI:N/S:U/C:L/I:N/A:N
cwe-id: CWE-1021
cwe-name: Improper Restriction of Rendered UI Layers or Frames
compliance:
  HIPAA: 164.306(a)
  ISO 27001: A.8.9
  owasp10: A5
  PCI-DSS v4.0.1: 6.2.4

---            

The Content Security Policy (CSP) is an HTTP header through which site owners define a set of security rules that the browser must follow when rendering their site. 
The most common usage is to define a list of approved sources of content that the browser can load. This can be used to effectively mitigate Cross-Site Scripting (XSS) and Clickjacking attacks.

CSP is flexible enough for you to define from where the browser can load JavaScript, Stylesheets, images, or fonts, among other options. It can also be used in report mode only, a recommended approach before deploying strict rules in a live environment. However, please note that report mode does not protect you, it just logs policy violations.

## How to fix

{% tabs insecure-content-security-policy %}
{% tab insecure-content-security-policy generic %}
You can define a Content Security Policy by setting a header in your application. The header can look like this:

	Content-Security-Policy: frame-ancestors 'none'; default-src 'self', script-src '*://*.example.com:*'

In this example, the **frame-ancestors** directive set to **'none'** indicates that the page cannot be placed inside a frame, not even by itself.
The **default-src** defines the loading policy for all resources, in this case, they can be loaded from the current origin (protocol + domain + port). The example sets a more specific policy for scripts, through the **script-src**, restricting script loading to any subdomain of example.com.

The policy can be with different directives, and there are other less strict options for the directives above.
{% endtab %}

{% endtabs %}
