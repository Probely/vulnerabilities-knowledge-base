---
name: MongoDB Injection
severity: high
cvss-score: 7.5
cvss-vector: CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:N/A:N
cwe-id: CWE-943
cwe-name: Improper Neutralization of Special Elements in Data Query Logic
compliance:
  HIPAA: 164.306(a)
  ISO 27001: A.5.33, A.5.34, A.8.3, A.8.12, A.8.25
  owasp10: A3
  pci: 6.5.1
  PCI-DSS v4.0.1: 6.2.4

---            

By abusing a poorly sanitized input, an attacker is able to exploit the application and inject arbitrary code into MongoDB. This vulnerability allows an attacker to tamper with existing MongoDB queries performed by the web application. Depending on the queries, the attacker might be able to access, modify or even destroy data from the database.

Since databases are commonly used to store private data, such as authentication information, personal user data, and site content, if an attacker gains access to it, the consequences are typically very severe, ranging from defacement of the web application to users data leakage or loss, or even full control of the web application or database server.

## How to fix

{% tabs mongodb-injection %}
{% tab mongodb-injection generic %}
Generating queries by hand is considered a bad practice and should be replaced by the most suitable application driver, as the MongoDB documentation recommends. In addition, sanitize all input, restricting it to only acceptable values. For instance, if the expected input is a number, ensure it matches a number, rejecting everything else. 

Keep in mind that if the attacker can also target the parameter name itself (example: "password[$ne]=2"), making it is necessary to be careful with both the name and the value of the parameter.
{% endtab %}

{% endtabs %}
