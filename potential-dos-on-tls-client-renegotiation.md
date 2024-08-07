---
name: Potential DoS on TLS Client Renegotiation
severity: low
cvss-score: 5.3
cvss-vector: CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:N/I:N/A:L
cwe-id: CWE-264
cwe-name: Permissions, Privileges, and Access Controls
compliance:
  HIPAA: 164.306(a), 164.312(c)(1), 164.312(e)(1)
  ISO 27001: A.5.14, A.8.9, A.8.24
  owasp10: A2
  pci: 4.1, 6.5.4
  PCI v4.0: pci4-4.2.1, pci4-6.2.4

---            

The server allows client-initiated renegotiation handshakes. Renegotiation allows a client to negotiate new session parameters, such as a new cipher suite. 

When a client starts a new TLS connection, the server will expend more CPU resources than the client. The client may exploit this resource usage asymmetry to launch a DoS attack. It may request a large number of renegotiation attempts until the server runs out of CPU. 

The CVE for this type of vulnerability is CVE-2011-1473.

## How to fix

{% tabs potential-dos-on-tls-client-renegotiation %}
{% tab potential-dos-on-tls-client-renegotiation generic %}
TLS 1.3 explicitly forbids renegotiation, since it closes a window of opportunity for an attack.

A strong argument in favor of disabling renegotiation is the fact that none of the world's top 5 sites by traffic allow renegotiation. If they serve most of the world and they don't need renegotiation, the remaining question is: do you really have a valid reason for allowing renegotiation?
{% endtab %}

{% endtabs %}
