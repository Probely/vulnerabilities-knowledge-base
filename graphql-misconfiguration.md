---
name: GraphQL Misconfiguration
severity: low
cvss-score: 5.3
cvss-vector: CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:L/I:N/A:N
cwe-id: CWE-200
cwe-name: Information Exposure
compliance:
  ISO 27001: A.8.9
  owasp10: A5

---            

The application server is leaking information about its schema or system internals. 

Attackers can exploit this weakness by submitting invalid queries to the GraphQL application, which, if misconfigured, will provide suggestions for potential query fixes. This unintentional behavior leaks valuable schema information.


Additionally, if the application returns a stack trace when an error occurs it can leak information about the code and the server.

## How to fix

{% tabs graphql-misconfiguration %}
{% tab graphql-misconfiguration generic %}
To mitigate this issue you should disable GraphQL fix suggestions and stack traces on your server configuration.
{% endtab %}

{% endtabs %}
