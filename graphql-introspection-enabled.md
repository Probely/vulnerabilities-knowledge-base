---
name: GraphQL Introspection enabled
severity: low
cvss-score: 5.3
cvss-vector: CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:L/I:N/A:N
cwe-id: '200'
cwe-name: Information Exposure
compliance:
  ISO 27001: A.8.9
  owasp10: A5

---            

GraphQL is an alternative to REST APIs, providing a query and manipulation language to the application dataset.
GraphQL Introspection is a feature that allows querying all the details of the supported API schema. An attacker can use it to obtain all the API's queries, types, fields, and directives, which in turn, can be abused to retrieve potentially sensitive information or to deliver injection attacks on the API endpoints.
The more attack surface an attacker has access to, the more likely it is to find a vulnerability.

## How to fix

{% tabs graphql-introspection-enabled %}
{% tab graphql-introspection-enabled generic %}
The safest solution is to disable GraphQL Introspection. However, you can also leave Introspection enabled based on context information such as the environment or the requesting user or role.
Please consult your GraphQL framework documentation for the correct way to disable it, or restrict access.
{% endtab %}

{% endtabs %}
