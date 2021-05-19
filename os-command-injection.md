
# Name

OS command injection

# Severity

High

# CVSS Score

9.8

# CVSS Vector

CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H

# CWE ID

CWE-77

# CWE NAME 

Command Injection

# Affected Compliance

OWASP Top 10: A1

PCI-DSS: 6.5.1

# Description

A command injection vulnerability allows the attacker to execute arbitrary operating system commands on the server. In the worst case scenario, the attacker will be able to fully administrate the server, which will enable him to extract sensitive data, modify the application contents or delete data.

These attacks happen when user supplied data (forms, cookies, HTTP headers etc.) is passed into a function that executes shell commands, without being properly sanitized. Because this sanitization is usually hard, it is recommended to avoid executing shell commands within the application, especially those with user supplied input. Instead use the APIs your language provides you.



# Generic How-to fix

The best way to fix and prevent this vulnerability is to replace the calls to the system/shell with calls to the API of the programming language. 

You should replace calls like `exec` or `system` with the matching function provided by your programming language. For instance, instead of using something like `system("rm $file");` to delete a file, use `remove($file);`. Typical functions you should avoid are `exec`, `system` and `call`.

If that is not an option, you should escape what is passed to those calls to ensure no malicious commands are executed. Each language will have its own escape functions, such as `escapeshellcmd` for PHP or `shellescape` for Ruby.

Finally, if the previous mitigations are not an option, you should strongly consider to _whitelist_ the characters that may be passed as argument to the function to avoid including malicious commands. To implement the _whitelist_ start by allowing only alphanumerical characters. You may allow more characters, but do not allow characters like `&`, `|`, `;` or `=`. In addition, run your application with the lowest privileges possible, and never as `root`. 
