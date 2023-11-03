---
name: Secure Renegotiation is not supported
severity: low
cvss-score: 7.4
cvss-vector: CVSS:3.0/AV:N/AC:H/PR:N/UI:N/S:U/C:H/I:H/A:N
cwe-id: CWE-264
cwe-name: Permissions, Privileges, and Access Controls
compliance:
  ISO 27001: A.5.14, A.8.9, A.8.24
  owasp10: A2
  pci: 4.1, 6.5.4

---            

This SSL/TLS implementation does not appear to handle renegotiation handshakes properly. This may allow an attacker to insert malicious data into the HTTPS connection. A malicious renegotiation allows clients and servers to modify the encryption parameters of an existing connection, for instance to require a weaker authentication mechanism.

To successfully exploit this vulnerability, the attacker must be able to perform a man-in-the-middle attack, which typically means the attacker is physically close to either the target server or the target victim. This situation is more likely to occur in wireless connections.

The CVE for this type of vulnerability is CVE-2009-3555.

## How to fix

{% tabs secure-renegotiation-is-not-supported %}
{% tab secure-renegotiation-is-not-supported generic %}
You can fix this problem by disabling support for the insecure renegotiation or by enabling support only for secure renegotiation. Secure renegotiation implements a different handshake for the renegotiation, making it unfeasible for the attacker to trigger the attack without being detected by either the client or the server.
{% endtab %}

{% endtabs %}
