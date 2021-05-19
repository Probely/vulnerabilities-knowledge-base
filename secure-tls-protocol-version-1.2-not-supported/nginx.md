To fix this issue, you need to enable TLS 1.2+ in your webserver configuration.

The following guidelines should help you enabling TLS 1.2+ with a strong cipher suite.

For the Nginx server configuration use this snippet as guideline:

```
server {
    listen 443 ssl;
    ...
    ssl_protocols TLSv1.2 TLSv1.3;
    ...
}
```

We have written an in-depth article about modern TLS deployments [here](https://blog.probely.com/how-to-deploy-modern-tls-in-2018-1b9a9cafc454).