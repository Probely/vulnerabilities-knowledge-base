---
name: Mixed content
severity: low
cvss-score: 6.5
cvss-vector: CVSS:3.0/AV:N/AC:H/PR:N/UI:N/S:U/C:H/I:L/A:N
cwe-id: CWE-319
cwe-name: Cleartext Transmission of Sensitive Information
compliance:
  HIPAA: 164.306(a), 164.312(c)(1), 164.312(e)(1)
  ISO 27001: A.5.14, A.8.24
  owasp10: A2
  pci: 4.1, 6.5.4

---            

The application is loaded over an HTTPS connection but it loads resources over an unencrypted connection, in HTTP. If an attacker is strategically positioned between the victim and the applications it can eavesdrop all communications between them. In this case, it would only be able to eavesdrop the resource loaded over HTTP, but it could modify its contents to affect other parts of the application, even if they are loaded over a secure connection.

A possible scenario would be for the attacker to modify some JavaScript content, loaded over HTTP, that handles the login form submission. Suppose the destination host of the login request is defined in the JavaScript file and the attacker changes it to host controlled by him, thus getting access to the victim's credentials.

## How to fix

{% tabs mixed-content %}
{% tab mixed-content generic %}
All resources present in the page must be loaded over HTTPS, including those served from third-party services, such as those used for analytics.

Resources provided by third-parties are normally available over HTTPS, and most of the times is just a matter of replacing `http` with `https`. However, you should always consult the documentation of the service to ensure you are loading the resource from the proper URL.

For resources that are not available over HTTPS, you can create a HTTPS reverse proxy that loads the resource with HTTP and serve it over HTTPS.
{% endtab %}

{% endtabs %}
