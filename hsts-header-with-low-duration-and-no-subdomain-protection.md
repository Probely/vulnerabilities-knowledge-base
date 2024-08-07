---
name: HSTS header with low duration and no subdomain protection
severity: low
cvss-score: 4.8
cvss-vector: CVSS:3.0/AV:N/AC:H/PR:N/UI:N/S:U/C:L/I:L/A:N
cwe-id: CWE-319
cwe-name: Cleartext Transmission of Sensitive Information
compliance:
  HIPAA: 164.306(a), 164.312(c)(1), 164.312(e)(1)
  ISO 27001: A.5.14, A.8.9, A.8.24
  owasp10: A2, A5
  pci: 4.1, 6.5.4
  PCI v4.0: pci4-4.2.1, pci4-6.2.4

---            

The application is setting the `Strict-Transport-Security` header but with insecure values, specifically with a low `max-age` value and without the `subdomains` option. A low `max-age` value means browsers will remember that the site is only to be accessed using HTTPS for a short time. Every time the `max-age` expires, the browser will allow HTTP requests to be made to the site, thus putting whatever information is being transmitted at risk of being intercepted by an attacker. The lower the value, the more likely for HTTP requests to be allowed and more chances of putting the information at risk.

The `includeSubdomains` option will extend the benefit of the header to the subdomains, preventing situations where the attacker registers (or takes over) a subdomain and leverages that read session cookies from the parent domain.

## How to fix

{% tabs hsts-header-with-low-duration-and-no-subdomain-protection %}
{% tab hsts-header-with-low-duration-and-no-subdomain-protection generic %}
The application should set the `Strict-Transport-Security` header with secure values. You just need to increase the `max-age` value to a higher value and add the `includeSubdomains` option.

A secure header will look like this:
```
Strict-Transport-Security: max-age=15768000;includeSubdomains 
```

The `max-age` value is set to 6 months to increase the chances of the browser remembering that the site is only to be accessed using HTTPS, therefore protecting the user. If the user visits the site again in the 6 months window, which is likely if the user visits the site frequently, it will make the browser remember the setting for another 6 months, thus protecting the user almost constantly.

With the option `includeSubdomains`, all requests to URLs in the current domain and subdomains will go over HTTPS. When you set `includeSubdomains` make sure you can serve all requests over HTTPS! It is, however, important that you add the option `includeSubdomains` whenever is possible.
{% endtab %}

{% endtabs %}
