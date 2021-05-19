
# Name

Private IP addresses disclosed

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

# Description

Private IP addresses are only used within internal networks and are not routable outside these networks, namely to the Internet. Since these are only used by internal servers, exposing them may help the attacker create an successful attack, targeted at those IPs.

# Generic How-to fix

Fixing this type of issue depends on where in the response the private IP address is disclosed. Often the disclosed is in a responder header that indicates the server that handled the request. In this case, it should be replaced by generic identifiers, such as server1, server2, etc, or even disabled.

If the IP appears in an error message, please rewrite the message to hide any internal information about the application.
