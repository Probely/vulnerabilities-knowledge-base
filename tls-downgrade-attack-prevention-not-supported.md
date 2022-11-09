---
name: TLS Downgrade attack prevention not supported
severity: low
cvss-score: 7.4
cvss-vector: CVSS:3.0/AV:N/AC:H/PR:N/UI:N/S:U/C:H/I:H/A:N
cwe-id: CWE-757
cwe-name: Selection of Less-Secure Algorithm During Negotiation ('Algorithm Downgrade')
compliance:
  owasp10: A2
  pci: 4.1, 6.5.4

---            

The server does not prevent SSL/TLS protocol downgrade attacks, which may cause insecure connections to be established, despite being made over SSL/TLS. An attacker that can interfere with the connection can force the client to negotiate a weaker protocol and cipher suite with the server, and then take advantage of that cipher suite weakness to read or modify client-server connections.

For instance, even though a client may support the secure TLS 1.2 protocol, the attacker may force it to connect to the server using SSL 3.0, which is insecure, possibly allowing the attacker to decrypt and extract session cookies and other secrets.

TLS_FALLBACK_SCSV is sent by the client to inform the server that the connection is being retried with a lower version protocol. If the server sees TLS_FALLBACK_SCSV and it supports a higher protocol than the one advertised by the client, it will know there is no good reason for the client to be trying a lower protocol, and will prevent the connection, thus mitigating the attack.

For this attack to succeed, the attacker must be able to tamper with the connection between the client and the server, which is fairly easy if both the attacker and the client are in the same network, this is more likely if the client is using a wireless connection.

## How to fix

{% tabs tls-downgrade-attack-prevention-not-supported %}
{% tab tls-downgrade-attack-prevention-not-supported generic %}
To prevent any protocol downgrade attack the server must support a special cipher suite named TLS_FALLBACK_SCSV. To add support to it, you will likely need to update your web server or any SSL/TLS libraries it uses.
{% endtab %}

{% endtabs %}
