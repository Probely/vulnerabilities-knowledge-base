
# Name

Path traversal

# Severity

High

# CVSS Score

7.5

# CVSS Vector

CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:N/A:N

# CWE ID

CWE-22

# CWE NAME 

Improper Limitation of a Pathname to a Restricted Directory ('Path Traversal')

# Affected Compliance

OWASP Top 10: A5

PCI-DSS: 6.5.8

# Description

A path traversal vulnerability occurs when the application places user input in filesystem operations without proper care. The attacker explores this vulnerability, typically, with various sequences of dot-dot-slash (../) characters that change the file being read or written to one of his choice, possibly even outside of the root folder of the application. Other possibility is for the attacker to use absolute paths.

Typically, the successful exploration of these vulnerabilities has a very high impact since the attacker is able to access sensitive files from the application, either configuration files or source-code files. Depending on the vulnerability, the attacker may be able to read most files on the server.

This attack is also frequently referred to as Directory Traversal.

# Generic How-to fix

The most secure way of fixing a path traversal vulnerability is to prevent any user input from controlling which files are read by the application. This is only achievable if the application replaces the references to files being read with an indirect reference, such as index number than is then converted to a file name in the server. Something like `example.com?file=example.css` would become `example.com?file=1`.

A simpler solution would be to ensure the files being read are all contained in a base directory and it is not possible to read files outside that directory. To ensure that you need two steps:
* canonicalize the file that you want to read, which means converting it to its absolute and simplest representation
* then, extract the filename from the canonicalized path and concatenate it with your base directory.

All programming languages have functions that implement thise, such as `realpath()` and `basename()`. The resulting path will definitely point to a file within your base directory, thus limiting reading to the expected files.
