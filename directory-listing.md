---
name: Directory Listing
severity: low
cvss-score: 5.3
cvss-vector: CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:L/I:N/A:N
cwe-id: CWE-548
cwe-name: Exposure of Information Through Directory Listing
compliance:
  owasp10: A1

---            

A directory listing vulnerability means that the webserver lists the contents of its directories, allowing the attacker to easily browse all the files within the affected directories. Often, this causes sensitive files to be exposed to the world, such as internal reports, logs, backups and even the source code of the application.

Directory listing is a feature of the webserver, that can help users browse the content of a web site, much like an FTP server or a shared folder. There are legitimate reasons to have this feature enabled, but more frequently it is enabled inadvertently, typically because it is the default web server configuration. You should consider disabling it for the entire application, thus ensuring that no existing directories (or future ones) are vulnerable.

## How to fix

{% tabs directory-listing %}
{% tab directory-listing generic %}
Directory listing is a feature of the web server, thus you can disable it in its configuration file, either globally or per virtual host.

How to disable it is specific to the web server that you are using, and independent of the language of your application. The configuration can have different names depending on the web server you are using. Typical names are Directory Listing, Directory Browsing, Directory Indexing or Indexes.

For instance, in Apache 2.X server you disable it in the virtual host configuration file, with:
```
    Options -Indexes
```

In a Nginx server you disable it within the `server` block, in the virtual host configuration file, by adding:
```
    autoindex off;
```

If you are using IIS, you need to edit the `web.config` file and add `directoryBrowse` directive within your `system.webserver` settings:
```
    <configuration>
       <system.webServer>
          <directoryBrowse enabled="false" />
       </system.webServer>
    </configuration>
```

{% endtab %}

{% tab directory-listing nginx %}
Directory listing is a feature of the web server, thus you can disable it in its configuration file, either globally or per virtual host.

In the NGINX server you disable it within the `server` block, in the virtual host configuration file, by adding:
```
    autoindex off;
```


{% endtab %}

{% endtabs %}
