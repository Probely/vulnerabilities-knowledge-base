---
name: Reflected cross-site scripting
severity: high
cvss-score: 8.2
cvss-vector: CVSS:3.1/AV:N/AC:L/PR:N/UI:R/S:C/C:H/I:L/A:N
cwe-id: CWE-79
cwe-name: Improper Neutralization of Input During Web Page Generation ('Cross-site
  Scripting')
compliance:
  HIPAA: 164.306(a)
  ISO 27001: A.8.25
  owasp10: A3
  pci: 6.5.7
  PCI-DSS v4.0.1: 6.2.4

---            

A reflected cross-site scripting (XSS) vulnerability allows the attacker to temporarily inject malicious scripts in the application page. The typical attack is to send a link to the victim with some JavaScript in it, which will be executed in the victim's browser, inside the vulnerable page. This malicious JavaScript can, for instance, read the session cookie and send it to the attacker, change the login form and point it to a page controlled by the attacker (and thus stealing the credentials) or even add a non-existent form asking for sensitive data.

Depending on the type of XSS and the nature of the vulnerable application, the impact of this vulnerability can range from temporarily modifying the contents of the website (during the victim's visit) to total control of the victim's session or even of the browser. Given its prevalence and ease of exploitation, it's often considered a serious risk for any application that contains an area that requires authentication.

This type of vulnerability is quite widespread on the Internet and happens when the application takes user input and prints (outputs) it without properly encode or validate that input. The name _reflected_ comes from the malicious code that is sent to the server and reflected back to the victim's browser, in the source code of the page.

## How to fix

{% tabs reflected-cross-site-scripting %}
{% tab reflected-cross-site-scripting generic %}
The correct prevention method is to escape the user input data before including it in the response, however there are some rules you must follow to ensure proper escaping is applied.

If you are using a template system to define the look and layout of your application, it is likely that it has support for auto-escaping data, without much hassle. Depending on the system, you either enable it globally when loading the template system or you have to enable it everything time you echo some code or variable in the page.

Using a template system to generate your pages will probably save you some time and it easier to ensure that is XSS-free, since most of them auto-escape by design, such as the template system used in the Python framework Django.

If you have to do it by hand you must be aware that there isn't one-size-fits-all solution: the way you escape the input depends on the context of the page where it is being placed. There are four contexts where it is common to place user input. These are:

1. HTML body and HTML element attributes
1. JavaScript
1. CSS and style attributes
1. URI's

#### HTML Body and Element Attributes Context

This rule applies to data inserted into HTML body elements, such as `div`, `p`, `b`, `td`, etc. and also to simple attribute values like `width`, `name`, `value`, `id`, etc. It must not be used in attributes like `href`, `src`, `style`, or any event handler like `onmouseover`.

You should use an HTML encoding function, available in the most common programming languages, to encode all characters that have a special meaning in HTML, such as `<` ,  `>`, `&` , `"`  and `'`  to their corresponding entities representation `&lt;`,  `&gt;`, `&amp;`, `&quot;` and `&apos;`.

#### Javascript Context

This rules applies to input placed directly inside JavaScript code - both script blocks and event-handler attributes, such as `onmouseover`.

In this case you should escape any input by converting it to its unicode representation. For instance, `;` should become `\u003b`. If you don't have access to a function that does this conversion, you have the option to convert to the `\xHH` format, where `HH` its the character hex representation.

#### CSS and Style tag Context

To escape user data within CSS or within a style tag you should use the `\HHHHHH` format, where `HHHHHH` is hex representation of the character, padded with the necessary zeros.

#### URL GET Parameters Context

This context is for URL based attributes, such as `href` and `src`. Input within these should be passed through an URL encoding function. All languages have functions to perform such conversion, for instance, in Python you would use `urllib.urlencode`.


#### Alternative solution
Additionally you could validate the input, _i.e._, implement whitelist of characters that you allow in each field and only accept those values at the server if they are in the whitelist. If you only allow alphanumeric characters you will be safe, but if you add others you may be at risk, so always implement escaping. Validating the input is just an extra-measure but you should not rely on it.
{% endtab %}

{% tab reflected-cross-site-scripting php %}
The correct prevention method is to escape the user input data before including it in the response, however there are some rules you must follow to ensure proper escaping is applied.

If you are using a template system to define the look and layout of your application, it is likely that it has support for auto-escaping data, without much hassle. Depending on the system, you either enable it globally when loading the template system or you have to enable it everything time you echo some code or variable in the page.

Using a template system to generate your pages will probably save you some time and it easier to ensure that is XSS-free, since most of them auto-escape by design, such as the template system used in the Python framework Django.

If you have to do it by hand you must be aware that there isn't one-size-fits-all solution: the way you escape the input depends on the context of the page where it is being placed. There are four contexts where it is common to place user input. These are:

1. HTML body and HTML element attributes
1. JavaScript
1. CSS and style attributes
1. URI's

#### HTML Body and Element Attributes Context

This rule applies to data inserted into HTML body elements, such as `div`, `p`, `b`, `td`, etc. and also to simple attribute values like `width`, `name`, `value`, `id`, etc. It must not be used in attributes like `href`, `src`, `style`, or any event handler like `onmouseover`.

You should use `htmlspecialchars` in PHP, like this:

```
echo htmlspecialchars($string, ENT_QUOTES, 'UTF-8');
```

#### Javascript Context

This rules applies to input placed directly inside JavaScript code - both script blocks and event-handler attributes, such as `onmouseover`.

In this case you should escape any input by converting it to its unicode representation. For instance, `;` should become `\u003b`. If you don't have access to a function that does this conversion, you have the option to convert to the `\xHH` format, where `HH` its the character hex representation.

#### CSS and Style tag Context

To escape user data within CSS or within a style tag you should use the `\HHHHHH` format, where `HHHHHH` is hex representation of the character, padded with the necessary zeros.

#### URL GET Parameters Context

This context is for URL based attributes, such as `href` and `src`. Input within these should be passed through an URL encoding function. All languages have functions to perform such conversion, for instance, in Python you would use `urllib.urlencode`.
{% endtab %}

{% endtabs %}
