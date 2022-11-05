---
name: Secure TLS protocol version 1.2 not supported
severity: low
cvss-score: 5.4
cvss-vector: CVSS:3.0/AV:N/AC:H/PR:N/UI:N/S:C/C:L/I:L/A:N
cwe-id: CWE-326
cwe-name: Inadequate Encryption Strength
compliance:
  owasp10: A2
  pci: 4.1, 6.5.4

---            

TLS protocol version 1.2 is not enabled on your server. We strongly recommend that TLS 1.2 is enabled, as it is both safer and faster than previous versions and protocols.

One of the most important features of TLS 1.2 is that it supports AEAD ciphers (Authenticated Encryption with Associated Data). Some non-AEAD ciphers are vulnerable to a class of attacks called padding-oracles, which led to the publication of attacks such as Lucky Thirteen and POODLE, amongst others. Moreover, as of 2018, TLS 1.2 adoption is above 94%.
By supporting AEAD ciphers, TLS 1.2 is much more robust against padding-oracle attacks.

Additionally, depending on CPU support, some AEAD ciphers are actually faster to execute than their older counterparts.

## How to fix

{% tabs secure-tls-protocol-version-12-not-supported %}
{% tab secure-tls-protocol-version-12-not-supported generic %}
To fix this issue, you need to enable TLS 1.2+ in your webserver configuration. 

The following guidelines should help you enable TLS 1.2+ with a strong cipher suite. 

For the Apache server configuration, use this snippet as a guideline:


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


For the Nginx server configuration, the following snippet may be used as a guideline:


```
server {
    listen 443 ssl;

    ...

    ssl_protocols TLSv1.2 TLSv1.3;
    ssl_ciphers 'ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-CHACHA20-POLY1305:ECDHE-RSA-CHACHA20-POLY1305:ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-SHA384:ECDHE-RSA-AES256-SHA384:ECDHE-ECDSA-AES128-SHA256:ECDHE-RSA-AES128-SHA256';
    ssl_prefer_server_ciphers on;

    ....
}
```

We have written an in-depth article with more details [here](https://blog.probely.com/how-to-deploy-modern-tls-in-2018-1b9a9cafc454).
{% endtab %}

{% tab secure-tls-protocol-version-12-not-supported nginx %}
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
{% endtab %}

{% tab secure-tls-protocol-version-12-not-supported apache %}
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
{% endtab %}

{% endtabs %}
