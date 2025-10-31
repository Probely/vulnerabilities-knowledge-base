---
name: Session Token in URL
severity: medium
cvss-score: 5.9
cvss-vector: CVSS:3.1/AV:N/AC:H/PR:N/UI:R/S:U/C:H/I:L/A:N
cwe-id: CWE-200
cwe-name: Exposure of Sensitive Information to an Unauthorized Actor
compliance:
  HIPAA: 164.306(a)
  ISO 27001: A.8.2, A.8.3, A.8.25
  owasp10: A2, A7
  pci: 6.5.10
  PCI-DSS v4.0.1: 6.2.4

---            

Sensitive information transmitted in the URL may be logged in different locations such as the browser history, the web server logs and any proxy present between the client and the application. It may also be sent to third party sites through the referer header, just by following a link in the application.

It is also easier to inadvertently share the URL with the sensitive information with an accidental copy-paste or by sharing the URL in a social application.

In this case, the sensitive information is a session token. If the attacker gets this session token it can hijack the victim session and authenticate in the application as if was the victim, accessing is account.

## How to fix

{% tabs session-token-in-url %}
{% tab session-token-in-url generic %}
Applications should replace the usage of session tokens in the URL by session cookies, which is the recommended method to transmit session tokens in HTTP requests. 

The application should set a cookie using the adequate programming language function, which will result in an HTTP response with something similar to `Set-Cookie: sessionid=cppynyovhdltchrlezxusy44; HttpOnly; Secure`.



{% endtab %}

{% endtabs %}
