---
name: HSTS header set in HTTP
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

The application is setting the `Strict-Transport-Security` header but it is doing it over HTTP instead of over HTTPS and browsers ignore this header if it is being set over HTTP. This behavior is to prevent a self-inflicted denial-of-service attack on a site that is not prepared to serve HTTPS requests but because it set the header, browsers would only connect to it over HTTPS.
Because of this, the application does not force users to connect over an encrypted channel. If the user types the site address in the browser without starting with _https_, it will connect to it over an insecure channel, even if there is a redirect to HTTPS later. Even if the user types _https_, there may be links to the site in HTTP, forcing the user to navigate insecurely. An attacker that is able to intercept traffic between the victim and the site or spoof the site's address can prevent the user from ever connecting to it over an encrypted channel. This way, the attacker is able to eavesdrop all communications between the victim and the server, including the victim's credentials, session cookie and other sensitive information.

## How to fix

{% tabs hsts-header-set-in-http %}
{% tab hsts-header-set-in-http generic %}
The application should set the `Strict-Transport-Security` header only in HTTPS responses. 
To implement this behavior ensure the header is set only in the virtual host section that handles HTTPS connections, and remove it from the section that handles HTTP requests. This way the web server will only set the header in HTTPS responses.

If you are setting the header in the application, you may need to test if the request is coming over HTTP or HTTPS, and set it only for the HTTPS requests. It is easier to understand and manage if you set this header at the web server level and not in your application.

For reference, a properly set HSTS header will look like this:
```
Strict-Transport-Security: max-age=15768000;includeSubdomains 
```

When the browser sees this, it will remember, for the given number of seconds, that the current domain should only be contacted over HTTPS. In the future, if the user types _http://_ or omits the scheme, HTTPS is the default. In this example, which includes the option `includeSubdomains`, all requests to URLs in the current domain and subdomains will go over HTTPS. When you set `includeSubdomains` make sure you can serve all requests over HTTPS! It is, however, important that you add the option `includeSubdomains` whenever is possible. 

Note that because HSTS is a "trust on first use" (TOFU) protocol, a user who has never accessed the application will never have seen the HSTS header, and may therefore be vulnerable to aforementioned SSL stripping attacks. To mitigate this risk, you can optionally ask the browser vendors to include your domain in a preloaded list, included in the browser, and afterwards add the 'preload' flag to the HSTS header.
{% endtab %}

{% endtabs %}
