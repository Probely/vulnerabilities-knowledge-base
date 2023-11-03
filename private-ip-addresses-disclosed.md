---
name: Private IP addresses disclosed
severity: low
cvss-score: 5.3
cvss-vector: CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:L/I:N/A:N
cwe-id: CWE-200
cwe-name: Exposure of Sensitive Information to an Unauthorized Actor
compliance:
  ISO 27001: A.5.33, A.8.4, A.8.9, A.8.12
  owasp10: A1, A5

---            

Private IP addresses are only used within internal networks and are not routable outside these networks, namely to the Internet. Since these are only used by internal servers, exposing them may help the attacker create an successful attack, targeted at those IPs.

## How to fix

{% tabs private-ip-addresses-disclosed %}
{% tab private-ip-addresses-disclosed generic %}
Fixing this type of issue depends on where in the response the private IP address is disclosed. Often the disclosed is in a responder header that indicates the server that handled the request. In this case, it should be replaced by generic identifiers, such as server1, server2, etc, or even disabled.

If the IP appears in an error message, please rewrite the message to hide any internal information about the application.
{% endtab %}

{% endtabs %}
