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