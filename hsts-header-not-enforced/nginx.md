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
