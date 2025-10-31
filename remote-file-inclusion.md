---
name: Remote File Inclusion
severity: high
cvss-score: 7.5
cvss-vector: CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:N/A:N
cwe-id: CWE-98
cwe-name: Improper Control of Filename for Include/Require Statement in PHP Program
compliance:
  HIPAA: 164.306(a)
  ISO 27001: A.5.33, A.5.34, A.8.3, A.8.4, A.8.12, A.8.25
  pci: 6.5.1
  PCI-DSS v4.0.1: 6.2.4

---            

A remote file inclusion (RFI) vulnerability exists when an attacker can force the web application to load remote content. Depending on how the remote content is included it may lead to remote code execution (RCE). If the attacker is able to execute code on the server, he is very likely to access arbitrary content and take full control of the server.

RFI attacks usually occur when the application receives a path or URL as an input, uses that input to fetch some content, and then uses that same content to generate the response. 
One example that can lead to RCE is when the fetched content is loaded by the PHP `include` function. Similarly, if the fetched content is placed inside a template string, it can lead to a server-side template injection.

## How to fix

{% tabs remote-file-inclusion %}
{% tab remote-file-inclusion generic %}
To fix an RFI vulnerability, ensure only trusted input is included in the application. Depending on how your application is built, you have various options (that can, and should, be combined):
- Do not pass user input to include functions
- Whitelist the domains or files that can be passed as input to the include function and ensure nothing else goes through
- Validate the format of the input: if you don’t expect paths or URLs, reject inputs that have anything else other than alphanumeric characters.
{% endtab %}

{% endtabs %}
