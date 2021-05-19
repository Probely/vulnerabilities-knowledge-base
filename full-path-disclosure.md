
# Name

Full path disclosure

# Severity

Low

# CVSS Score

5.3

# CVSS Vector

CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:L/I:N/A:N

# CWE ID

CWE-200

# CWE NAME 

Exposure of Sensitive Information to an Unauthorized Actor

# Affected Compliance

PCI-DSS: 6.5.5

# Description

Full Path Disclosure vulnerabilities give the attacker information about the application internals, namely the path to a file hosted by the application server. Knowing the full path of files within the server can help the attacker explore other vulnerabilities, such as Path Traversal, Local File Include, and even SQL Injections.

By itself, this vulnerability does not pose an immediate risk to the application, since it is only giving away the location of a given file in the server. However, the name of the file and the enclosing folder name might reveal information that could be considered sensitive, if it gives advantage to a competitor.

# Generic How-to fix

To fix this vulnerability you need to prevent the full path from being displayed in the application. Depending on how the message is being generated you might need to change its contents or even disable verbose errors to the client altogether.

Disabling verbose errors is the best approach, since it prevents current and future errors from being displayed, without the need to change individual errors and logging.
