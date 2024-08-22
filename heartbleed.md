---
name: Heartbleed
severity: high
cvss-score: 7.5
cvss-vector: CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:N/A:N
cwe-id: CWE-126
cwe-name: Buffer over-read
compliance:
  HIPAA: 164.306(a)
  ISO 27001: A.5.33, A.5.34, A.8.3, A.8.9, A.8.12
  owasp10: A6
  PCI v4.0: pci4-6.2.4

---            

Heartbleed is a serious vulnerability in the OpenSSL library, which is used in many software that supports web applications, such as webservers. This vulnerability allows an attacker to steal sensitive information that is in the memory of the servers where OpenSSL is being used.
For instance, Heartbleed can be exploited to steal the private key associated with the certificate the server uses to deliver HTTPS, or even passwords from the users currently using the application.

This vulnerability has the CVE-2014-0160.

## How to fix

{% tabs heartbleed %}
{% tab heartbleed generic %}
The source of this vulnerability is the OpenSSL library, which is used by your webserver, for instance, to handle SSL/TLS connections.

The solution is to update the OpenSSL library to the most recent version. The first version of OpenSSL where this problem is fixed is 1.0.1g, so ensure that you have at least this version.
{% endtab %}

{% endtabs %}
