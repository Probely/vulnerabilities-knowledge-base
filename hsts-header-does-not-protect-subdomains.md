---
name: HSTS header does not protect subdomains
severity: low
cvss-score: 4.8
cvss-vector: CVSS:3.0/AV:N/AC:H/PR:N/UI:N/S:U/C:L/I:L/A:N
cwe-id: CWE-319
cwe-name: Cleartext Transmission of Sensitive Information
compliance:
  ISO 27001: A.5.14, A.8.9, A.8.24
  owasp10: A2, A5
  pci: 4.1, 6.5.4

---            

The application is setting the `Strict-Transport-Security` header but with an insecure value, specifically without the `includeSubdomains` option. 
The `includeSubdomains` option will extend the benefit of the header to the subdomains, preventing situations where the attacker registers (or takes over) a subdomain and leverages that read session cookies from the parent domain.

## How to fix

{% tabs hsts-header-does-not-protect-subdomains %}
{% tab hsts-header-does-not-protect-subdomains generic %}
The application should set the `Strict-Transport-Security` header with secure values. You just need to add the `includeSubdomains` option.

A secure header will look like this:
```
Strict-Transport-Security: max-age=15768000;includeSubdomains 
```

With the option `includeSubdomains`, all requests to URLs in the current domain and subdomains will go over HTTPS. When you set `includeSubdomains` make sure you can serve all requests over HTTPS! It is, however, important that you add the option `includeSubdomains` whenever is possible.
{% endtab %}

{% endtabs %}
