---
name: Hidden file found
severity: low
cvss-score: 5.3
cvss-vector: CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:L/I:N/A:N
cwe-id: CWE-538
cwe-name: File and Directory Information Exposure
compliance:
  HIPAA: 164.306(a), 164.312(a)(1), 164.312(d)
  ISO 27001: A.8.4, A.8.9, A.8.15
  owasp10: A1, A5

---            

We found a file in your application with potentially sensitive content. If attackers find it, they can use it to exploit or facilitate the exploitation of your application.

## How to fix

{% tabs hidden-file-found %}
{% tab hidden-file-found generic %}
If you don’t need this file to run your application, remove it from the server. If you need it, move it to somewhere not accessible to users or set proper access permissions.
{% endtab %}

{% endtabs %}
