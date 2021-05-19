
# Name

ASP.NET tracing enabled

# Severity

High

# CVSS Score

9.1

# CVSS Vector

CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:N

# CWE ID

CWE-11

# CWE NAME 

ASP.NET Misconfiguration: Creating Debug Binary

# Affected Compliance

OWASP Top 10: A6

PCI-DSS: 6.5.5

# Description

The ASP.NET tracing feature allows debugging of the web server interactions, by displaying full details of the requests and responses of all users visiting the site. These details are available in a well known URL that is accessible to any user, 
disclosing any sensitive information that is present there such as session tokens, credentials, private personal information and anything transmitted to and from the application.

An attacker that visits the ASP.NET trace page will easily hijack the accounts of any other user logged in the application just by using the session token it got there.


# Generic How-to fix

ASP.NET tracing is a feature of the ASP.NET framework, configured in the `web.config` file. To disable it, you need to edit the `web.config` file and change the `trace` directive within your `system.web` settings:
```
    <configuration>
       <system.web>
          <trace enabled="false" localOnly="true"/>
       </system.web>
    </configuration>
```

The `localOnly="true"` is a fail-safe in case the trace is enabled again. With this flag set to `true`, the trace page will only be available through the server itself, i.e. localhost, thus safe from requests from the Internet.
