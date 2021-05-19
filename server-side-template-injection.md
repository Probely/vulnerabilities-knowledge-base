
# Name

Server-side template injection

# Severity

High

# CVSS Score

5.3

# CVSS Vector

CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:L/I:N/A:N

# CWE ID

CWE-94

# CWE NAME 

Improper Control of Generation of Code ('Code Injection')

# Affected Compliance

OWASP Top 10: A1

PCI-DSS: 6.5.1

# Description

A server-side template injection vulnerability occurs when user input is placed in a server-side template. An attacker may be able to inject template directives with the objective of executing arbitrary code.
The impact of this vulnerability depends on various factors, such as the template engine and what characters can be used in the payload. The most straightforward attacks give the attacker the ability to read information that it should not have access to. In some cases, this type of vulnerability may give the attacker full control over the server.

# Generic How-to fix

The best recommendation is to avoid having templates depending on user input. Try to restrict any user input to template parameters and follow the template engine documentation on how to prevent injection vulnerabilities.
