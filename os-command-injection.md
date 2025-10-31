---
name: OS command injection
severity: critical
cvss-score: 9.8
cvss-vector: CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H
cwe-id: CWE-77
cwe-name: Command Injection
compliance:
  HIPAA: 164.306(a)
  ISO 27001: A.5.33, A.5.34, A.8.3, A.8.12, A.8.25
  owasp10: A3
  pci: 6.5.1
  PCI-DSS v4.0.1: 6.2.4

---            

A command injection vulnerability allows the attacker to execute arbitrary operating system commands on the server. In the worst case scenario, the attacker will be able to fully administrate the server, which will enable him to extract sensitive data, modify the application contents or delete data.

These attacks happen when user supplied data (forms, cookies, HTTP headers etc.) is passed into a function that executes shell commands, without being properly sanitized. Because this sanitization is usually hard, it is recommended to avoid executing shell commands within the application, especially those with user supplied input. Instead use the APIs your language provides you.



## How to fix

{% tabs os-command-injection %}
{% tab os-command-injection generic %}
The best way to fix and prevent this vulnerability is to replace the calls to the system/shell with calls to the API of the programming language. 

You should replace calls like `exec` or `system` with the matching function provided by your programming language. For instance, instead of using something like `system("rm $file");` to delete a file, use `remove($file);`. Typical functions you should avoid are `exec`, `system` and `call`.

If that is not an option, you should escape what is passed to those calls to ensure no malicious commands are executed. Each language will have its own escape functions, such as `escapeshellcmd` for PHP or `shellescape` for Ruby.

Finally, if the previous mitigations are not an option, you should strongly consider to _whitelist_ the characters that may be passed as argument to the function to avoid including malicious commands. To implement the _whitelist_ start by allowing only alphanumerical characters. You may allow more characters, but do not allow characters like `&`, `|`, `;` or `=`. In addition, run your application with the lowest privileges possible, and never as `root`. 
{% endtab %}

{% tab os-command-injection php %}
The best way to fix and prevent this vulnerability is to replace the calls to the system/shell with calls to the PHP API.

For instance, instead of using something like `system("rm ".$file");` to delete a file, use `unlink($file);`. The functions that can lead to this vulnerability, and thus that you should replace are `exec`, `shell_exec`, `system`, `passthru` and `proc_open` .

If replacement is not possible, you should escape what is passed to those calls to ensure no malicious commands are executed. In PHP you use `escapeshellcmd` and `escapeshellarg` to escaped the commands and arguments passed to the operating system, respectively.

```
    $cmd = "/bin/script";
    $args = "-d -c 2";
    $c = escapeshellcmd($cmd)." ".escapeshellarg($args);
    $output = system($c);
````
Finally, if the previous mitigations are not an option, you should strongly consider to _whitelist_ the characters that may be passed as argument to the function to avoid including malicious commands. To implement the _whitelist_ start by allowing only alphanumerical characters. You may allow more characters, but do not allow characters like `&`, `|`, `;` or `=`. In addition, run your application with the lowest privileges possible, and never as `root`.
{% endtab %}

{% endtabs %}
