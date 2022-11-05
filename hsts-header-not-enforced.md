---
name: HSTS header not enforced
severity: low
cvss-score: 7.4
cvss-vector: CVSS:3.0/AV:N/AC:H/PR:N/UI:N/S:U/C:H/I:H/A:N
cwe-id: CWE-319
cwe-name: Cleartext Transmission of Sensitive Information
compliance:
  owasp10: A2, A5
  pci: 4.1, 6.5.4

---            

The application does not force users to connect over an encrypted channel, i.e. over HTTPS. If the user types the site address in the browser without starting with _https_, it will connect to it over an insecure channel, even if there is a redirect to HTTPS later. Even if the user types _https_, there may be links to the site in HTTP, forcing the user to navigate insecurely. An attacker that is able to intercept traffic between the victim and the site or spoof the site's address can prevent the user from ever connecting to it over an encrypted channel. This way, the attacker is able to eavesdrop all communications between the victim and the server, including the victim's credentials, session cookie and other sensitive information.

## How to fix

{% tabs hsts-header-not-enforced %}
{% tab hsts-header-not-enforced generic %}
The application should instruct web browsers to only access the application using HTTPS. To do this, enable HTTP Strict Transport Security (HSTS).

You can do so by sending the `Strict-Transport-Security` header so that browsers will always enforce a secure connection to your site, regardless of the user typing _https_ in the address.

An HSTS enabled server includes the following header in an HTTPS response: 
```
Strict-Transport-Security: max-age=15768000;includeSubdomains 
```
Please bear in mind that only HTTPS responses should have the HSTS header, because browsers ignore this header when sent over HTTP.

When the browser sees this, it will remember, for the given number of seconds, that the current domain should only be contacted over HTTPS. In the future, if the user types _http://_ or omits the scheme, HTTPS is the default. In this example, which includes the option `includeSubdomains`, all requests to URLs in the current domain and subdomains will go over HTTPS. When you set `includeSubdomains` make sure you can serve all requests over HTTPS! It is, however, important that you add the option `includeSubdomains` whenever is possible. 

Instead of changing your application, you should have the web server setting the header for you. If you are using Apache, just enable `mod_headers` and add the following line to your virtual host configuration: 
```
Header always set Strict-Transport-Security "max-age=15768000;includeSubdomains"
```

If you are using NGINX, just add this line to your host configuration: 
```
add_header Strict-Transport-Security max-age=15768000;includeSubdomains
```

Note that because HSTS is a "trust on first use" (TOFU) protocol, a user who has never accessed the application will never have seen the HSTS header, and may therefore be vulnerable to aforementioned SSL stripping attacks. To mitigate this risk, you can optionally ask the browser vendors to include your domain in a preloaded list, included in the browser, and afterwards add the 'preload' flag to the HSTS header.
{% endtab %}

{% tab hsts-header-not-enforced nginx %}
The application should instruct web browsers to only access the application using HTTPS. To do this, enable HTTP Strict Transport Security (HSTS).

You can do so by sending the `Strict-Transport-Security` header so that a browser that supports HSTS will always enforce a secure connection to your site on all subsequent requests. This will prevent some passive and active attacks such as _sslstrip_.

An HSTS enabled server includes the following header in an HTTPS reply: 
```
Strict-Transport-Security: max-age=15768000;includeSubdomains 
```

When the browser sees this, it will remember, for the given number of seconds, that the current domain should only be contacted over HTTPS. In the future, if the user types _http://_ or omits the scheme, HTTPS is the default. In this example, which includes the option includeSubdomains, all requests to URLs in the current domain and subdomains will be redirected to HTTPS. When you set `includeSubdomains` make sure you can serve all requests over HTTPS! It is, however, important that you add the option `includeSubdomains` whenever is possible. 

Instead of changing your application, you can have the web server doing this for you. 

You should add the following line to your NGINX host configuration: 
```
add_header Strict-Transport-Security max-age=15768000;includeSubdomains
```
Note that because HSTS is a "trust on first use" (TOFU) protocol, a user who has never accessed the application will never have seen the HSTS header, and will therefore still be vulnerable to SSL stripping attacks. To mitigate this risk, you can optionally add the 'preload' flag to the HSTS header, and submit the domain for review by browser vendors.

{% endtab %}

{% endtabs %}
