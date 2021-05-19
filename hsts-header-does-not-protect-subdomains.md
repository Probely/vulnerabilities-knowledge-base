
# Name

HSTS header does not protect subdomains

# Severity

Low

# CVSS Score

4.8

# CVSS Vector

CVSS:3.0/AV:N/AC:H/PR:N/UI:N/S:U/C:L/I:L/A:N

# CWE ID

CWE-319

# CWE NAME 

Cleartext Transmission of Sensitive Information

# Affected Compliance

OWASP Top 10: A3, A6

PCI-DSS: 4.1, 6.5.4

# Description

The application is setting the `Strict-Transport-Security` header but with an insecure value, specifically without the `includeSubdomains` option. 
The `includeSubdomains` option will extend the benefit of the header to the subdomains, preventing situations where the attacker registers (or takes over) a subdomain and leverages that read session cookies from the parent domain.

# Generic How-to fix

The application should set the `Strict-Transport-Security` header with secure values. You just need to add the `includeSubdomains` option.

A secure header will look like this:
```
Strict-Transport-Security: max-age=15768000;includeSubdomains 
```

With the option `includeSubdomains`, all requests to URLs in the current domain and subdomains will go over HTTPS. When you set `includeSubdomains` make sure you can serve all requests over HTTPS! It is, however, important that you add the option `includeSubdomains` whenever is possible.
