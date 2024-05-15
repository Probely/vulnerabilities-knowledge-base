---
name: 'Cross Origin Resource Sharing: Arbitrary Origin Trusted'
severity: low
cvss-score: 6.1
cvss-vector: CVSS:3.0/AV:N/AC:L/PR:N/UI:R/S:C/C:L/I:L/A:N
cwe-id: CWE-942
cwe-name: Permission Cross-Domain Policy with Untrusted Domains
compliance:
  HIPAA: 164.306(a), 164.312(a)(1), 164.312(d)
  ISO 27001: A.8.2, A.8.3
  owasp10: A1
  pci: 6.5.8

---            

An HTML5 Cross-Origin Resource Sharing (CORS) policy controls whether and how content running on other domains can perform two-way interaction with the domain that publishes the policy. The policy is fine-grained and can apply access controls per-request based on the URL and other features of the request.  

If another domain is allowed by the policy, then that domain can potentially attack users of the application. If a user is logged in to the application, and visits a domain allowed by the policy, then any malicious content running on that domain can potentially retrieve content from the application, and sometimes carry out actions within the security context of the logged-in user.  

The aforementioned impact is exploitable because the site specifies the header Access-Control-Allow-Credentials: true and allows any arbitrary origin to bypass same-origin policy as can be seen in the response header Access-Control-Allow-Origin.

Even if an allowed domain is not overtly malicious in itself, security vulnerabilities within that domain could potentially be leveraged by an attacker to exploit the trust relationship and attack the application that allows access. CORS policies on pages containing sensitive information should be reviewed to determine whether it is appropriate for the application to trust both the intentions and security posture of any domains granted access.

## How to fix

{% tabs cross-origin-resource-sharing-arbitrary-origin-trusted %}
{% tab cross-origin-resource-sharing-arbitrary-origin-trusted generic %}
Any inappropriate domains should be removed from the CORS policy or you should only send the header Access-Control-Allow-Origin to origins that you allow, i.e., you should use a whitelist of trusted domains.
{% endtab %}

{% endtabs %}
