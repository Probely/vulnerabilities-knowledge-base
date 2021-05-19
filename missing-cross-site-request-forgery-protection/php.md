To prevent a CSRF you need to add a secret token to the vulnerable form (or the URL, if the vulnerable action is a GET). You generate a per-session token and add it to the user session:

```
    if (isLoginValid($username, $password)) {
        session_regenerate_id();
        $_SESSION["csrf_token"] = bin2hex(openssl_random_pseudo_bytes(32));
        // if you are using PHP 7 you can use the line below instead
        // $_SESSION["csrf_token"] = bin2hex(random_bytes(32));
    }
    else {
        echo "invalid username or password";
        return;
    }
```

Then, every time you generate a form, add the token to a hidden field:

```  
    <form action="profile.php" method="post">
        <input type="hidden" name="token" value="<?php echo $_SESSION["csrf_token"];?>"<br>
        New email: <input type="email" name="email"><br>
        <input type="submit">
    </form>
```

Finally, you need to check if the token is right when receiving the form. If its right, the form submission is legit. If not you just prevented an CSRF attack.

```
    if (array_key_exists("csrf_token", $_POST) && $_POST["csrf_token"] === $_SESSION["csrf_token"]) {
        // form is valid, proceed
    }
    else {
        // form is invalid, do not proceed
    }
```