---
name: XML external entity injection
severity: high
cvss-score: 7.5
cvss-vector: CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:N/A:N
cwe-id: CWE-611
cwe-name: Improper Restriction of XML External Entity Reference
compliance:
  HIPAA: 164.306(a)
  ISO 27001: A.8.9
  owasp10: A5

---            

An XML External Entity Injection vulnerability occurs when the application processes a XML that contains user input while allowing references to external entities. External entities work like placeholders in the XML that typically refer to a local or remote file. In a legitimate use, these files may be external DTD, stylesheets or external schemas, but an attacker may point them to local files which will be read by the XML parser and included in the XML, and maybe displayed in the application instead of the legitimate XML content.

The range of possible attacks is very wide and it is highly dependent on how the application processes the XML. Another scenario is to include an entity that points to a local file in the server, say `/etc/passwd` and another entity that points to a remove file, with the contents of the other entity as a parameter. This attack will read `/etc/passwd` and sent its contents to an attacker controlled server, through HTTP. 
In this scenario there is no need to read the contents of the XML, or the results of its parsing, at the application, since the data is leaking to an external server.

## How to fix

{% tabs xml-external-entity-injection %}
{% tab xml-external-entity-injection generic %}
To fix and prevent injection of XML External Entity, processing of external entities should be disabled in your XML parser. This is usually done by setting a flag when loading or parsing the XML. Make your you disable all types of entities since there a few of them.

If you cannot disable external entities in your parser, use a strict input validation limiting the characters that reach the XML structure. The ideal solution is to allow only alphanumeric characters (or even less, depending on your application), thus preventing the attacker from breaking the XML structure and inject entities.
{% endtab %}

{% endtabs %}
