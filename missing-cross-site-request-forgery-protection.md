
# Name

Missing cross-site request forgery protection

# Severity

Low

# CVSS Score

6.5

# CVSS Vector

CVSS:3.0/AV:N/AC:L/PR:N/UI:R/S:U/C:N/I:H/A:N

# CWE ID

CWE-352

# CWE NAME 

Cross-Site Request Forgery (CSRF)

# Affected Compliance

OWASP Top 10: A2

PCI-DSS: 6.5.9, 6.5.10

# Description

Cross-Site Request Forgery (CSRF) is an attack that forces an end user to execute unwanted actions on the vulnerable application in which they're currently authenticated. Suppose your are logged-in in your application and the attacker sends you a seemingly inoffensive link that you click. That link will open a page that forces your browser to do a request to your application, with your session cookie. If that request is to the change email address page, the attacker just changed your email address on the application to his. With that it is likely that he can recover your password and login.

Typically, all state-changing operations in your page must be protected against CSRF, even those with a confirmation screen, or else the attacker will likely be able to change that page state without your knowledge.

This vulnerability is known by other names also: XSRF, Sea Surf and Session Riding.

# Generic How-to fix

To prevent a CSRF you need to add a secret token to the vulnerable form (or the URL, if the vulnerable action is a GET), and validate if the token is echoed back when receiving the form. If it is, the form submission is legit and you can proceed. If it is not, then you should reject the post data.

The most practical place to store the the token is associated with the user session, and can be the same during the whole session. However, it should be different between sessions, even if from the same user. The token should be 32 bytes, random and unpredictable. You can use a function that generates secure random values (such as openssl_random_pseudo_bytes) or use the sha256 of the session identifier, which is also a token with the desired properties, so its sha256 will also be. 

Then, for each form you generate, add the token as an hidden field:

    <form action="profile.php" method="post">
        <input type="hidden" name="token" value="9ff731ca4727ffad98d1eae1b2dd3172a4cfbc08fd52fc8dd022db998ec5b517"<br>
        New email: <input type="email" name="email"><br>
        <input type="submit">
    </form>

When the server receives the form, it validates if the token value is the same that was stored in the session, and if that is the case, everything is fine.

If you are using a framework to build your application, it is likely that it has a setting to enable these tokens without any extra code, you just need to check the configuration file or the documentation and enable the CSRF protection (it might appear as _forgery_ protection).
