
# Name

Inclusion of cryptocurrency mining script

# Severity

High

# CVSS Score

5.5

# CVSS Vector

CVSS:3.0/AV:N/AC:H/PR:L/UI:R/S:C/C:L/I:L/A:L

# CWE ID

CWE-830

# CWE NAME 

Inclusion of Web Functionality from an Untrusted Source

# Affected Compliance

# Description

Your application is including a JavaScript library known to abuse the computing resources of the victim's computer to mine cryptocurrencies. 

The presence of this type of libraries is usually a strong indicator that your application has been compromised (which allowed the attacker to add the malicious content).

Clients connecting to your web application will turn into victims while this malicious JavaScript uses their computing power, making the device slower. Clients will notice their CPU going to 100% when visiting your site, affecting your application reputation. In addition, your web application may be marked as malicious and be blocked by security controls, such as those present in modern browsers, preventing your customers from reaching the site.

# Generic How-to fix

Stop including the malicious JavaScript library in the site by deleting all references to it. 

Please note that your web application may have been hacked through another vulnerability that allowed the attacker to insert this library. It's also possible, but less likely, that an employee with access to the code/server may have changed the application for his/her own profit.
