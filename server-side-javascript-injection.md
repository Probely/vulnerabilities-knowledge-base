
# Name

Server-side JavaScript injection

# Severity

High

# CVSS Score

7.3

# CVSS Vector

CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:L/I:L/A:L

# CWE ID

CWE-94

# CWE NAME 

Improper Control of Generation of Code ('Code Injection')

# Affected Compliance

OWASP Top 10: A1

PCI-DSS: 6.5.1

# Description

A Server-side JavaScript injection vulnerability allows the attacker to run arbitrary JavaScript code on the server. Web Applications that pass user input to functions like `eval()`, `setTimeout()` and `setInterval()` are potentially vulnerable.

The impact of this vulnerability ranges from an effective denial-of-service attack to File System access on the server.

# Generic How-to fix

To prevent a Server-side JavaScript injection vulnerability, you should validate all user input on the server-side before processing. 

You should also consider the following:
* Do not use the `eval()` function to parse user inputs. 
* If you need to parse JSON input, use a safer alternative such as `JSON.parse()`.
* Include "```use strict```" at the beginning of a function.
