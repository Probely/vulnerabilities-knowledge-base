
# Name

Missing clickjacking protection

# Severity

Low

# CVSS Score

6.5

# CVSS Vector

CVSS:3.0/AV:N/AC:L/PR:N/UI:R/S:U/C:N/I:H/A:N

# CWE ID

CWE-1021

# CWE NAME 

Improper Restriction of Rendered UI Layers or Frames

# Affected Compliance

OWASP Top 10: A6

# Description

A **frameable response** occurs when one or multiple pages can be used on an iframe on any website. This allows the **clickjacking** attack to be used. 

**Clickjacking** is when an attacker a hidden iframe with multiple transparent or opaque layers above it, to trick a user into clicking on a button or link on the iframe when they were intending to click on the the top level page. Thus, the attacker is "hijacking" clicks meant for the top level page and routing them to the iframe.

Using a similar technique, keystrokes can also be hijacked. With a carefully crafted combination of stylesheets, iframes, and text boxes, a user can be led to believe they are typing in the password to their email or bank account, but are instead typing into an invisible frame controlled by the attacker.

# Generic How-to fix

The recommended way to prevent clickjacking is to send a header that instructs the browser to not allow arbitrary framing, typically from other domains.

The current recommendation is to use the Content-Security-Policy HTTP header (CSP) with a **frame-ancestors** directive. This header obsoletes the X-Frame-Options HTTP header.

To use CSP you need the following header:

	Content-Security-Policy: frame-ancestors 'none'

The header might contain more directives, and there are other less strict options for the **frame-ancestors** directive.

<br>
If you want to use X-Frame-Options, send the proper HTTP header, with one of the following directives:

	X-Frame-Options: DENY  
	X-Frame-Options: SAMEORIGIN

A third directive, **ALLOW-FROM** is no longer supported by modern browsers. 

If you specify **DENY**, all attempts to load the page in a frame will fail. **SAMEORIGIN** will allow the page to be loaded in the site including it in a frame is the same as the one serving the page. 

The most common option is **DENY** when there is no need to load your pages on some other site.
