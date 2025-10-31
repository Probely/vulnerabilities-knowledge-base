---
name: Open redirection
severity: medium
cvss-score: 8.2
cvss-vector: CVSS:3.1/AV:N/AC:L/PR:N/UI:R/S:C/C:L/I:H/A:N
cwe-id: CWE-601
cwe-name: URL Redirection to Untrusted Site ('Open Redirect')
compliance:
  HIPAA: 164.306(a)
  ISO 27001: A.8.25
  PCI-DSS v4.0.1: 6.2.4

---            

The Open Redirection vulnerability occurs because it is possible to force the application to do an HTTP redirect to an arbitrary domain, chosen by the attacker.

The attacker can construct a URL to the application that, when visited, redirects the victim to the attacker site. Because the first request is made to a legitimate domain, it can be leveraged to create realistic and successful phishing attacks, since users will trust the URL and will likely not notice the redirect to the malicious domain. This technique is also useful to bypass security controls that look for malicious domains in URLs.

## How to fix

{% tabs open-redirection %}
{% tab open-redirection generic %}
You can fix an open redirect by either preventing user input from being used in the target redirection or by validating the user input before the redirection.

If you known in advance the URLs to where you need to redirect you can remove the redirection functionality, thus removing the vulnerability. If that is the case, you can replace each redirect by a direct link to the target URL.
You can also have a server-side list of target URLs and pass in the parameter a reference to the right index of that list.

If you need to have user input in the redirection parameter you can take a few measures to reduce the likelihood of an successful attack:
* validate the URL domain with a whitelist of domains you trust
* if you only need to redirect to your domain, allow only relative URLs by validating if they start with a single slash character and then prepend http://youdomain.example to the URL
* if you only need to redirect to your domain, allow only absolute URLs by validating if it starts with http://yourdomain.example/.
{% endtab %}

{% endtabs %}
