
# Name

ASP.NET ViewState without MAC

# Severity

Low

# CVSS Score

5.3

# CVSS Vector

CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:N/I:L/A:N

# CWE ID

CWE-642

# CWE NAME 

External Control of Critical State Data

# Affected Compliance

OWASP Top 10: A6

# Description

The View state is a mechanism implemented by the ASP.NET framework to maintain the state of the web form controls and other data between requests. The state is serialized by the server and kept in the `__VIEWSTATE` hidden field. This field is read back by the server to render pages at the right state. 

The problem arises when the view state is used by the server to control the application logic and, because it is not protected by a MAC validation code, the attacker can modify its contents to gain unauthorised access. Suppose the user role is defined in the view state and the attacker changes his low privilege role to admin: the server will read the view state without noticing it was tampered with, and render the page as if the attacker was admin.

# Generic How-to fix

The View state is a feature of the ASP.NET framework, configured in the `web.config` file. To enable the MAC validation for the View state you need to edit the `web.config` file and change the `trace` directive within your `system.web` settings:
```
    <configuration>
       <system.web>
          <pages enableViewStateMac="true">
       </system.web>
    </configuration>
```

Like many settings of ASP.NET, this one can also be enabled only for a single page with `<%@ Page EnableViewStateMac="true" %>`. However, this is not recommended because its prone to errors where new pages, or forgotten ones, are not properly protected, so you should only set this in the `web.config` file and remove any page configuration of `EnableViewStateMac`.
