---
name: Insecure PHP Object deserialization
severity: high
cvss-score: 7.3
cvss-vector: CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:L/I:L/A:L
cwe-id: CWE-502
cwe-name: Deserialization of Untrusted Data
compliance:
  HIPAA: 164.306(a), 164.312(c)(1)
  ISO 27001: A.8.25
  owasp10: A8
  PCI-DSS v4.0.1: 6.2.4

---            

An Insecure PHP Object deserialization vulnerability potentially allows an attacker to execute arbitrary code in the application, which can result in a total compromise of the application security.
These vulnerabilities occur when the attacker is able to input strings with serialized PHP objects, which are then read by a vulnerable unserialize function call.

These attacks are not frequently seen as they are target specific, which makes mass exploitation difficult. A complete compromise of the application is hard to achieve because there are multiple conditions to be met. However, damage to the application might still be possible even if not all the requirements are met.

## How to fix

{% tabs insecure-php-object-deserialization %}
{% tab insecure-php-object-deserialization generic %}
The safest approach is to stop accepting serialized objects that can be tainted by the user.
If you need to use PHP object serialization, we strongly recommend you to use an HMAC, generated and validated server-side, on all serialized objects. This will ensure that serialized objects are not modified by the user in any way.

Alternatively, consider replacing the existing serialization format with a safe, standard data interchange format such as JSON.
{% endtab %}

{% endtabs %}
