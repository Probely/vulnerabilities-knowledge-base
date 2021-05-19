Directory listing is a feature of the web server, thus you can disable it in its configuration file, either globally or per virtual host.

In the NGINX server you disable it within the `server` block, in the virtual host configuration file, by adding:
```
    autoindex off;
```

