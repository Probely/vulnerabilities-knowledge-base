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