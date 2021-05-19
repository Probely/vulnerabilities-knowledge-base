
# Name

HSTS header not enforced

# Severity

Low

# CVSS Score

7.4

# CVSS Vector

CVSS:3.0/AV:N/AC:H/PR:N/UI:N/S:U/C:H/I:H/A:N

# CWE ID

CWE-319

# CWE NAME 

Cleartext Transmission of Sensitive Information

# Affected Compliance

OWASP Top 10: A3, A6

PCI-DSS: 4.1, 6.5.4

# Description

The application does not force users to connect over an encrypted channel, i.e. over HTTPS. If the user types the site address in the browser without starting with _https_, it will connect to it over an insecure channel, even if there is a redirect to HTTPS later. Even if the user types _https_, there may be links to the site in HTTP, forcing the user to navigate insecurely. An attacker that is able to intercept traffic between the victim and the site or spoof the site's address can prevent the user from ever connecting to it over an encrypted channel. This way, the attacker is able to eavesdrop all communications between the victim and the server, including the victim's credentials, session cookie and other sensitive information.

# Generic How-to fix

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
Header add Strict-Transport-Security "max-age=15768000;includeSubdomains"
```

If you are using NGINX, just add this line to your host configuration: 
```
add_header Strict-Transport-Security max-age=15768000;includeSubdomains
```

Note that because HSTS is a "trust on first use" (TOFU) protocol, a user who has never accessed the application will never have seen the HSTS header, and may therefore be vulnerable to aforementioned SSL stripping attacks. To mitigate this risk, you can optionally ask the browser vendors to include your domain in a preloaded list, included in the browser, and afterwards add the 'preload' flag to the HSTS header.
