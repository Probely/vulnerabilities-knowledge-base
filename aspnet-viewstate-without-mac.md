---
name: ASP.NET ViewState without MAC
severity: low
cvss-score: 5.3
cvss-vector: CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:N/I:L/A:N
cwe-id: CWE-642
cwe-name: External Control of Critical State Data
compliance:
  HIPAA: 164.306(a)
  ISO 27001: A.8.9
  owasp10: A5
  PCI v4.0: pci4-6.2.4

---            

The View state is a mechanism implemented by the ASP.NET framework to maintain the state of the web form controls and other data between requests. The state is serialized by the server and kept in the `__VIEWSTATE` hidden field. This field is read back by the server to render pages at the right state. 

The problem arises when the view state is used by the server to control the application logic and, because it is not protected by a MAC validation code, the attacker can modify its contents to gain unauthorised access. Suppose the user role is defined in the view state and the attacker changes his low privilege role to admin: the server will read the view state without noticing it was tampered with, and render the page as if the attacker was admin.

## How to fix

{% tabs aspnet-viewstate-without-mac %}
{% tab aspnet-viewstate-without-mac generic %}
The View state is a feature of the ASP.NET framework, configured in the `web.config` file. To enable the MAC validation for the View state you need to edit the `web.config` file and change the `trace` directive within your `system.web` settings:
```
    <configuration>
       <system.web>
          <pages enableViewStateMac="true">
       </system.web>
    </configuration>
```

Like many settings of ASP.NET, this one can also be enabled only for a single page with `<%@ Page EnableViewStateMac="true" %>`. However, this is not recommended because its prone to errors where new pages, or forgotten ones, are not properly protected, so you should only set this in the `web.config` file and remove any page configuration of `EnableViewStateMac`.
{% endtab %}

{% endtabs %}
