---
name: ASP.NET tracing enabled
severity: high
cvss-score: 9.1
cvss-vector: CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:N
cwe-id: CWE-11
cwe-name: 'ASP.NET Misconfiguration: Creating Debug Binary'
compliance:
  HIPAA: 164.306(a)
  ISO 27001: A.5.33, A.5.34, A.8.4, A.8.9, A.8.12
  owasp10: A5
  pci: 6.5.5
  PCI v4.0: pci4-6.2.4

---            

The ASP.NET tracing feature allows debugging of the web server interactions, by displaying full details of the requests and responses of all users visiting the site. These details are available in a well known URL that is accessible to any user, 
disclosing any sensitive information that is present there such as session tokens, credentials, private personal information and anything transmitted to and from the application.

An attacker that visits the ASP.NET trace page will easily hijack the accounts of any other user logged in the application just by using the session token it got there.


## How to fix

{% tabs aspnet-tracing-enabled %}
{% tab aspnet-tracing-enabled generic %}
ASP.NET tracing is a feature of the ASP.NET framework, configured in the `web.config` file. To disable it, you need to edit the `web.config` file and change the `trace` directive within your `system.web` settings:
```
    <configuration>
       <system.web>
          <trace enabled="false" localOnly="true"/>
       </system.web>
    </configuration>
```

The `localOnly="true"` is a fail-safe in case the trace is enabled again. With this flag set to `true`, the trace page will only be available through the server itself, i.e. localhost, thus safe from requests from the Internet.
{% endtab %}

{% endtabs %}
