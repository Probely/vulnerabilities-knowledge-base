To fix a vulnerability of this type, you just need to set the HttpOnly flag on the vulnerable cookie, effectively preventing it from being read by client side scripts.

In PHP, to set HttpOnly in the session cookie, you edit the `php.ini` file and add `session.cookie_httponly = True`. You can set it at application level, if you can't edit `php.ini`. In this case, use the `session_set_cookie_params` function, with the `httponly` parameter `true`:

```
    session_set_cookie_params(0, '/', '.example.com', true, true); 
```

If this is not a session cookie, but a regular application cookie, you must set the last parameter of your `setcookie` call to true:

```
    setcookie("OtherCookie", $value, time()+3600, "/", "example.com", true, true);
```