
# Name

Insecure Silverlight clientaccesspolicy.xml policy

# Severity

High

# CVSS Score

6.5

# CVSS Vector

CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:L/I:L/A:N

# CWE ID

CWE-942

# CWE NAME 

Permissive Cross-domain Policy with Untrusted Domains

# Affected Compliance

OWASP Top 10: A6

# Description

The clientaccesspolicy.xml file defines how Silverlight applications from other domains can interact with the domain hosting this policy file.

An `<domain uri="*"/>` directive inside a `allow-from` section in your clientaccesspolicy.xml file means that your application allows an arbitrary Silverlight application (.xap files) running on an arbitrary domain to make requests to your domain and read its response. If a user is logged in your application and visits a site hosting a malicious Silverlight application, that application can make authenticated requests on behalf of the user to your application, by sending the cookies your site sets. With this, it can potentially take control of the victim's account.

If this vulnerability was reported as low severity, it means that Probe.ly does not have the required context to determine the impact of this issue. You are allowing any arbitrary Silverlight application running on any subdomain of your domain to make requests to your site and read its response. If you do not host any user-content on the subdomain specified in your policy then it is safe to ignore this vulnerability.

# Generic How-to fix

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
