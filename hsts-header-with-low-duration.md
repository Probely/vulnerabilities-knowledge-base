---
name: HSTS header with low duration
severity: low
cvss-score: 7.4
cvss-vector: CVSS:3.0/AV:N/AC:H/PR:N/UI:N/S:U/C:H/I:H/A:N
cwe-id: CWE-319
cwe-name: Cleartext Transmission of Sensitive Information
compliance:
  owasp10: A2, A5
  pci: 4.1, 6.5.4

---            

The application is setting the `Strict-Transport-Security` header but with an insecure value, specifically with a low `max-age` value. A low `max-age` value means browsers will remember that the site is only to be accessed using HTTPS for a short time. Every time the `max-age` expires, the browser will allow HTTP requests to be made to the site, thus putting whatever information is being transmitted at risk of being intercepted by an attacker. The lower the value, the more likely for HTTP requests to be allowed and more chances of putting the information at risk.

## How to fix

{% tabs hsts-header-with-low-duration %}
{% tab hsts-header-with-low-duration generic %}
The application should set the `Strict-Transport-Security` header with secure values. You just need to increase the `max-age` value to a higher value.

A secure header will look like this:
```
Strict-Transport-Security: max-age=15768000;includeSubdomains 
```

The `max-age` value is set to 6 months to increase the chances of the browser remembering that the site is only to be accessed using HTTPS, therefore protecting the user. If the user visits the site again in the 6 months window, which is likely if the user visits the site frequently, it will make the browser remember the setting for another 6 months, thus protecting the user almost constantly.
{% endtab %}

{% endtabs %}
