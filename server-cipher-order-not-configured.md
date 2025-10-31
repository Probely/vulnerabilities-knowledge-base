---
name: Server Cipher Order not configured
severity: high
cvss-score: 4.2
cvss-vector: CVSS:3.0/AV:A/AC:H/PR:N/UI:N/S:U/C:L/I:L/A:N
cwe-id: CWE-757
cwe-name: Selection of Less-Secure Algorithm During Negotiation ('Algorithm Downgrade')
compliance:
  HIPAA: 164.306(a), 164.312(c)(1), 164.312(e)(1)
  ISO 27001: A.5.14, A.8.9, A.8.24
  owasp10: A2
  pci: 4.1, 6.5.4
  PCI-DSS v4.0.1: 4.2.1, 6.2.4

---            

The server does not define a preferred order in which the cipher suites are chosen, thus giving priority to the client's cipher suite list, which will make some clients choose the first one from the list. This is an insecure behavior since clients may not send the more secure cipher suites first, causing the SSL/TLS handshake to negotiate with weaker cipher suites that were only enabled for compatibility with older clients.

Connections negotiated with less secure cipher suites will be at risk if an attacker is able to eavesdrop the communications, something that is likely if the victim is using an wireless connection and the attacker is in its vicinity.

## How to fix

{% tabs server-cipher-order-not-configured %}
{% tab server-cipher-order-not-configured generic %}
The server should set the order of the cipher suites it supports, typically with the most secure first and force that order to be honored. 
The correct configuration is server-specific but typically requires changing two settings:  the cipher suite list correctly ordered, from the most secure to the least secure, and enabling the cipher suite server order honoring.

Depending on the situation there may be a tradeoff between putting the most secure or faster cipher suites first.
{% endtab %}

{% endtabs %}
