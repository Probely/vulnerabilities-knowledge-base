
# Name

ASP.NET debugging enabled

# Severity

Low

# CVSS Score

5.3

# CVSS Vector

CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:L/I:N/A:N

# CWE ID

CWE-489

# CWE NAME 

Active Debug Code

# Affected Compliance

OWASP Top 10: A6

PCI-DSS: 6.5.5

# Description

The ASP.NET debug feature is useful for debugging ASP.NET web applications, and even be used for remote debugging. This feature can reveal sensitive information about the internals of the application, such as code snippets, environment variables, security keys, etc. All of this can be used by an attacker to increase the likelihood of an successful attack.

This debug feature should not be enabled in a production environment.


# Generic How-to fix

ASP.NET debugging is a feature of the ASP.NET framework, configured in the `web.config` file. To disable it, you need to edit the `web.config` file and change the `debug` flag within your `compilation` directive to `false`:

```
    <configuration>  
        <system.web>  
            <compilation  
                debug="false"  
                ...  
            >  
            ...  
            </compilation>  
        </system.web>  
    </configuration>  

```
