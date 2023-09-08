---
name: Hidden File Found
severity: low
cvss-score: 5.3
cvss-vector: CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:L/I:N/A:N
cwe-id: CWE-538
cwe-name: File and Directory Information Exposure
compliance: {}

---            

We found a file in your application with potentially sensitive content. If attackers find it, they can use it to exploit or facilitate the exploitation of your application.

## How to fix

{% tabs hidden-file-found %}
{% tab hidden-file-found generic %}
If you don’t need this file to run your application, remove it from the server. If you need it, move it to somewhere not accessible to users or set proper access permissions.
{% endtab %}

{% endtabs %}
