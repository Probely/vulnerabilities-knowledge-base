---
name: Insecure Silverlight clientaccesspolicy.xml policy
severity: high
cvss-score: 6.5
cvss-vector: CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:L/I:L/A:N
cwe-id: CWE-942
cwe-name: Permissive Cross-domain Policy with Untrusted Domains
compliance:
  HIPAA: 164.306(a)
  ISO 27001: A.8.2, A.8.3, A.8.9
  owasp10: A5

---            

The clientaccesspolicy.xml file defines how Silverlight applications from other domains can interact with the domain hosting this policy file.

An `<domain uri="*"/>` directive inside a `allow-from` section in your clientaccesspolicy.xml file means that your application allows an arbitrary Silverlight application (.xap files) running on an arbitrary domain to make requests to your domain and read its response. If a user is logged in your application and visits a site hosting a malicious Silverlight application, that application can make authenticated requests on behalf of the user to your application, by sending the cookies your site sets. With this, it can potentially take control of the victim's account.

If this vulnerability was reported as low severity, it means that Probe.ly does not have the required context to determine the impact of this issue. You are allowing any arbitrary Silverlight application running on any subdomain of your domain to make requests to your site and read its response. If you do not host any user-content on the subdomain specified in your policy then it is safe to ignore this vulnerability.

## How to fix

{% tabs insecure-silverlight-clientaccesspolicyxml-policy %}
{% tab insecure-silverlight-clientaccesspolicyxml-policy generic %}
To fix this vulnerability you should consider if your application needs to be accessed by Silverlight applications (.xap files). Few applications have this requirement.

If you don't have this requirement, you can safely delete the file, thus fixing the vulnerability.

If you need the file, and you know which domains hosting Silverlight files need to contact your application, you can whitelist those domains by listing each one in the file:

```
<allow-from http-request-headers="SOAPAction">
<domain uri="domain1.example.com"/>
<domain uri="domain2.example.com"/>
</allow-from>
```
Only Silverlight applications from these domains will be able to interact both-ways with your domain.

If you need arbitrary domains interacting with yours, you should consider hosting the endpoints that will be accessed in a isolated domain, different from the main one. Do not use a subdomain for this. With this isolation, you will be sure that requests from Silverlight applications will not carry your main domain session cookies, and will not be able to access the account of the user.
{% endtab %}

{% endtabs %}
