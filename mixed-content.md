
# Name

Mixed content

# Severity

Low

# CVSS Score

7.7

# CVSS Vector

CVSS:3.0/AV:N/AC:H/PR:N/UI:N/S:U/C:H/I:H/A:L

# CWE ID

CWE-319

# CWE NAME 

Cleartext Transmission of Sensitive Information

# Affected Compliance

OWASP Top 10: A3

PCI-DSS: 4.1, 6.5.4

# Description

The application is loaded over an HTTPS connection but it loads resources over an unencrypted connection, in HTTP. If an attacker is strategically positioned between the victim and the applications it can eavesdrop all communications between them. In this case, it would only be able to eavesdrop the resource loaded over HTTP, but it could modify its contents to affect other parts of the application, even if they are loaded over a secure connection.

A possible scenario would be for the attacker to modify some JavaScript content, loaded over HTTP, that handles the login form submission. Suppose the destination host of the login request is defined in the JavaScript file and the attacker changes it to host controlled by him, thus getting access to the victim's credentials.

# Generic How-to fix

All resources present in the page must be loaded over HTTPS, including those served from third-party services, such as those used for analytics.

Resources provided by third-parties are normally available over HTTPS, and most of the times is just a matter of replacing `http` with `https`. However, you should always consult the documentation of the service to ensure you are loading the resource from the proper URL.

For resources that are not available over HTTPS, you can create a HTTPS reverse proxy that loads the resource with HTTP and serve it over HTTPS.
