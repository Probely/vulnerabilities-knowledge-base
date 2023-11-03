---
name: Path traversal
severity: high
cvss-score: 7.5
cvss-vector: CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:N/A:N
cwe-id: CWE-22
cwe-name: Improper Limitation of a Pathname to a Restricted Directory ('Path Traversal')
compliance:
  ISO 27001: A.5.33, A.5.34, A.8.3, A.8.4, A.8.12, A.8.26
  owasp10: A1
  pci: 6.5.8

---            

A path traversal vulnerability occurs when the application places user input in filesystem operations without proper care. The attacker explores this vulnerability, typically, with various sequences of dot-dot-slash (../) characters that change the file being read or written to one of his choice, possibly even outside of the root folder of the application. Other possibility is for the attacker to use absolute paths.

Typically, the successful exploration of these vulnerabilities has a very high impact since the attacker is able to access sensitive files from the application, either configuration files or source-code files. Depending on the vulnerability, the attacker may be able to read most files on the server.

This attack is also frequently referred to as Directory Traversal.

## How to fix

{% tabs path-traversal %}
{% tab path-traversal generic %}
The most secure way of fixing a path traversal vulnerability is to prevent any user input from controlling which files are read by the application. This is only achievable if the application replaces the references to files being read with an indirect reference, such as index number than is then converted to a file name in the server. Something like `example.com?file=example.css` would become `example.com?file=1`.

A simpler solution would be to ensure the files being read are all contained in a base directory and it is not possible to read files outside that directory. To ensure that you need two steps:
* canonicalize the file that you want to read, which means converting it to its absolute and simplest representation
* then, extract the filename from the canonicalized path and concatenate it with your base directory.

All programming languages have functions that implement thise, such as `realpath()` and `basename()`. The resulting path will definitely point to a file within your base directory, thus limiting reading to the expected files.
{% endtab %}

{% endtabs %}
