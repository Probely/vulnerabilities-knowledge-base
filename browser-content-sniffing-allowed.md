
# Name

Browser content sniffing allowed

# Severity

Low

# CVSS Score

4.7

# CVSS Vector

CVSS:3.0/AV:N/AC:H/PR:N/UI:R/S:C/C:L/I:L/A:N

# CWE ID

CWE-16

# CWE NAME 

Configuration

# Affected Compliance

OWASP Top 10: A6

# Description

The application allows browsers to try to mime-sniff the content-type of the responses. This means the browser may try to guess the content-type by looking at the response content, and render it in way it was not intended to. This behavior may lead to the execution of malicious code, for instance, to explore an XSS vulnerability.

Applications should disable this behavior, forcing browsers to honor the content-type specified in the response. Without a specific content-type set browsers will default to render the content as text, turning XSS payloads innocuous.

Disabling mime-sniffing should be seen as an extra layer of defense against XSS, and not as replacement of the recommended XSS prevention techniques.

# Generic How-to fix

This problem can be fixed by sending the header **X-Content-Type-Options** with value **nosniff**, to force browsers to disable the content-type guessing (the sniffing).

The header should look this:

	X-Content-Type-Options: nosniff

It is normally easy to enable the header in the web server configuration file, but it can also be done at application level.
