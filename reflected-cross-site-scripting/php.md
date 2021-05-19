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