To fix this issue you need to disable TLS 1.0. We also recommend that higher TLS protocol versions are enabled, ideally version 1.2 and above.

For most systems, enabling or disabling TLS versions requires a change on the web server configuration file. Therefore, refer to your web server documentation on how to do that.

For Nginx, you may use the following snippet as a guideline:

```
server {
    listen 443 ssl;
    ...
    ssl_protocols TLSv1.2 TLSv1.3;
    ...
}
```

Note that we are enabling TLS 1.2 and above, reflecting our ideal scenario.

If you need to cater to clients with very old TLS support, such as ancient mobile devices, and know what you are doing, you can keep TLS 1.0 enabled, despite the known weaknesses. These issues are not as serious as the SSL protocol weaknesses, but you should weight the need to support older clients with the risk of exposing private data. Moreover, keep in mind that TLS 1.2 support is well over [95%](https://blog.probely.com/how-to-deploy-modern-tls-in-2018-1b9a9cafc454).