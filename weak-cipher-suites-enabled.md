---
name: Weak cipher suites enabled
severity: medium
cvss-score: 7.4
cvss-vector: CVSS:3.0/AV:N/AC:H/PR:N/UI:N/S:U/C:H/I:H/A:N
cwe-id: CWE-326
cwe-name: Inadequate Encryption Strength
compliance:
  owasp10: A2
  pci: 4.1, 6.5.4

---            

The server supports weak cipher suites for SSL/TLS connections. These cipher suites are currently considered broken and, depending on the specific cipher suite, offer poor or no security at all. Thus defeating the purpose of using a secure communication channel in the first place.

Any connection to the server using a weak cipher suite is at risk of being eavesdropped and tampered with by an attacker that can intercept connections. This is more likely to occur to Wi-Fi clients.

Depending on the cipher suites used, a connection may be at an immediate risk of being intercepted.

## How to fix

{% tabs weak-cipher-suites-enabled %}
{% tab weak-cipher-suites-enabled generic %}
To stop using weak cipher suites, you must configure your web server cipher suite list accordingly.

Ideally, as a general guideline, you should remove any cipher suite containing references to NULL, anonymous, export, DES, 3DES, RC4, and MD5 algorithms. Additionally, remove any cipher suite containing ciphers with less than 128 bit security. You should also remove any CBC ciphers, as CBC ciphers may be vulnerable to padding oracle attacks. 

You should enable ECDHE and GCM cipher suites to ensure proper security. Please note that these modern ciphers are available in newer versions of TLS only. You will need to enable TLSv1.2 and above (for GCM cipher suites).

To achieve this, we propose a modern cipher suite, based on these [recommendations](https://blog.probely.com/how-to-deploy-modern-tls-in-2018-1b9a9cafc454):

  * `TLS13-AES-256-GCM-SHA384:TLS13-CHACHA20-POLY1305-SHA256:TLS13-AES-128-GCM-SHA256:ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-CHACHA20-POLY1305:ECDHE-RSA-CHACHA20-POLY1305:ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-SHA384:ECDHE-RSA-AES256-SHA384:ECDHE-ECDSA-AES128-SHA256:ECDHE-RSA-AES128-SHA256`

For most systems, changing TLS cipher suites, requires a change on the web server configuration file. Please refer to your web server documentation on how to do so.
{% endtab %}

{% tab weak-cipher-suites-enabled nginx %}
To stop using weak cipher suites, you must configure your web server cipher suite list accordingly.

Ideally, as a general guideline, you should remove any cipher suite containing references to NULL, anonymous, export, DES, 3DES, RC4, and MD5 algorithms. Additionally, remove any cipher suite containing ciphers with less than 128 bit security. You should also remove any CBC ciphers, as CBC ciphers may be vulnerable to padding oracle attacks. 

You should enable ECDHE and GCM cipher suites to ensure proper security. Please note that these modern ciphers are available in newer versions of TLS only. You will need to enable TLSv1.2 and above (for GCM cipher suites).

To achieve this, we propose a modern cipher suite, based on these [recommendations](https://blog.probely.com/how-to-deploy-modern-tls-in-2018-1b9a9cafc454):

  * `TLS13-AES-256-GCM-SHA384:TLS13-CHACHA20-POLY1305-SHA256:TLS13-AES-128-GCM-SHA256:ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-CHACHA20-POLY1305:ECDHE-RSA-CHACHA20-POLY1305:ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-SHA384:ECDHE-RSA-AES256-SHA384:ECDHE-ECDSA-AES128-SHA256:ECDHE-RSA-AES128-SHA256`

For NGINX, you can use the following snippet to enable the modern compatibility cipher suite. This will support TLS 1.2 and above only.

```
server {
    listen 443 ssl;
    ...
    ssl_protocols TLSv1.2 TLSv1.3;
    ssl_ciphers 'TLS13-AES-256-GCM-SHA384:TLS13-CHACHA20-POLY1305-SHA256:TLS13-AES-128-GCM-SHA256:ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-CHACHA20-POLY1305:ECDHE-RSA-CHACHA20-POLY1305:ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-SHA384:ECDHE-RSA-AES256-SHA384:ECDHE-ECDSA-AES128-SHA256:ECDHE-RSA-AES128-SHA256';
    ...
}
```
{% endtab %}

{% tab weak-cipher-suites-enabled apache %}
To stop using weak cipher suites, you must configure your web server cipher suite list accordingly.

Ideally, as a general guideline, you should remove any cipher suite containing references to NULL, anonymous, export, DES, 3DES, RC4, and MD5 algorithms. Additionally, remove any cipher suite containing ciphers with less than 128 bit security. You should also remove any CBC ciphers, as CBC ciphers may be vulnerable to padding oracle attacks. 

You should enable ECDHE and GCM cipher suites to ensure proper security. Please note that these modern ciphers are available in newer versions of TLS only. You will need to enable TLSv1.2 and above (for GCM cipher suites).

To achieve this, we propose a modern cipher suite, based on these [recommendations](https://blog.probely.com/how-to-deploy-modern-tls-in-2018-1b9a9cafc454):

  * `TLS13-AES-256-GCM-SHA384:TLS13-CHACHA20-POLY1305-SHA256:TLS13-AES-128-GCM-SHA256:ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-CHACHA20-POLY1305:ECDHE-RSA-CHACHA20-POLY1305:ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-SHA384:ECDHE-RSA-AES256-SHA384:ECDHE-ECDSA-AES128-SHA256:ECDHE-RSA-AES128-SHA256`

For the Apache server, the following snippet may be used to enable TLS 1.2+ and strong ciphers.

```
<VirtualHost *:443>
    ...
    SSLEngine on
    SSLProtocol                 -all +TLS1.2 +TLS1.3
    SSLCipherSuite            TLS13-AES-256-GCM-SHA384:TLS13-CHACHA20-POLY1305-SHA256:TLS13-AES-128-GCM-SHA256:ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-CHACHA20-POLY1305:ECDHE-RSA-CHACHA20-POLY1305:ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-SHA384:ECDHE-RSA-AES256-SHA384:ECDHE-ECDSA-AES128-SHA256:ECDHE-RSA-AES128-SHA256
    SSLHonorCipherOrder   on
    SSLCompression           off
    ...
</VirtualHost>```
{% endtab %}

{% endtabs %}
