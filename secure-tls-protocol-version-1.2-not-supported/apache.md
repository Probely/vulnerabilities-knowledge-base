To fix this issue, you need to enable TLS 1.2+ in your webserver configuration.

The following guidelines should help you enabling TLS 1.2+ with a strong cipher suite.

For the Apache server configuration use this snippet as guideline:


```
<VirtualHost *:443>
    ...

    SSLProtocol                -all +TLSv1.2 +TLSv1.3
    SSLCipherSuite           ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-CHACHA20-POLY1305:ECDHE-RSA-CHACHA20-POLY1305:ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-SHA384:ECDHE-RSA-AES256-SHA384:ECDHE-ECDSA-AES128-SHA256:ECDHE-RSA-AES128-SHA256 
    SSLHonorCipherOrder  on
    SSLCompression          off

    ...
</VirtualHost>

```

We have written a in-depth article about modern TLS deployments [here](https://blog.probely.com/how-to-deploy-modern-tls-in-2018-1b9a9cafc454).