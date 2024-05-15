---
name: Full path disclosure
severity: low
cvss-score: 5.3
cvss-vector: CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:L/I:N/A:N
cwe-id: CWE-200
cwe-name: Exposure of Sensitive Information to an Unauthorized Actor
compliance:
  HIPAA: 164.306(a)
  ISO 27001: A.8.4, A.8.9
  pci: 6.5.5

---            

Full Path Disclosure vulnerabilities give the attacker information about the application internals, namely the path to a file hosted by the application server. Knowing the full path of files within the server can help the attacker explore other vulnerabilities, such as Path Traversal, Local File Include, and even SQL Injections.

By itself, this vulnerability does not pose an immediate risk to the application, since it is only giving away the location of a given file in the server. However, the name of the file and the enclosing folder name might reveal information that could be considered sensitive, if it gives advantage to a competitor.

## How to fix

{% tabs full-path-disclosure %}
{% tab full-path-disclosure generic %}
To fix this vulnerability you need to prevent the full path from being displayed in the application. Depending on how the message is being generated you might need to change its contents or even disable verbose errors to the client altogether.

Disabling verbose errors is the best approach, since it prevents current and future errors from being displayed, without the need to change individual errors and logging.
{% endtab %}

{% tab full-path-disclosure suspected-wordpress %}
By default, Wordpress installations expose some PHP files that when directly accessed through a browser will show an error that includes a full path from the application server, if you allow the application to display errors to clients.

The root problem, in this case, is that your application shows these errors to whoever visits that URL. 
Errors should be handled properly in the application, without being echoed to the client. Careful programming can handle most errors in a way they are caught and logged internally but not to the client. If errors need to be displayed to the client, they should be masked and displayed with friendly texts without any internal information.

Wordpress uses PHP, so you need to set the PHP `display_errors` directive to off to prevent clients from viewing those error messages.
Depending on the technology used in the application, this can be configured at the framework level by enabling or disabling a setting, normally related to the displaying of errors. 


For instance, if you use php-fpm you need to change the php-fpm configuration file. Most of the times it will be one of these:

`/etc/php-fpm.d/<yourdomain>.conf` (per virtual host configuration)

`/etc/php-fpm.conf` (if you have a single php-fpm configuration)


<br>
In any case, add or uncomment the following line:

```
    php_flag[display_errors] = off
```


For other PHP installations, where the application reads a PHP ini file, use the following syntax:

```
    display_errors = Off
```
{% endtab %}

{% endtabs %}
