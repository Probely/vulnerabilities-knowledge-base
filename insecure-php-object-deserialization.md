
# Name

Insecure PHP Object deserialization

# Severity

High

# CVSS Score

6.5

# CVSS Vector

CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:L/I:L/A:N

# CWE ID

CWE-502

# CWE NAME 

Deserialization of Untrusted Data

# Affected Compliance

OWASP Top 10: A8

# Description

An Insecure PHP Object deserialization vulnerability potentially allows an attacker to execute arbitrary code in the application, which can result in a total compromise of the application security.
These vulnerabilities occur when the attacker is able to input strings with serialized PHP objects, which are then read by a vulnerable unserialize function call.

These attacks are not frequently seen as they are target specific, which makes mass exploitation difficult. A complete compromise of the application is hard to achieve because there are multiple conditions to be met. However, damage to the application might still be possible even if not all the requirements are met.

# Generic How-to fix

The safest approach is to stop accepting serialized objects that can be tainted by the user.
If you need to use PHP object serialization, we strongly recommend you to use an HMAC, generated and validated server-side, on all serialized objects. This will ensure that serialized objects are not modified by the user in any way.

Alternatively, consider replacing the existing serialization format with a safe, standard data interchange format such as JSON.
