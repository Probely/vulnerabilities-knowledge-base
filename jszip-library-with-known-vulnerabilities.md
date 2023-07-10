---
name: JSZip library with known vulnerabilities
severity: low
cvss-score: 4.8
cvss-vector: CVSS:3.0/AV:N/AC:H/PR:N/UI:N/S:U/C:L/I:L/A:N
cwe-id: CWE-1035
cwe-name: OWASP Top Ten 2017 Category A9 - Using Components with Known Vulnerabilities
compliance: {}

---            

The application uses an outdated version of the JSZip library, which has known vulnerabilities.

## How to fix

{% tabs jszip-library-with-known-vulnerabilities %}
{% tab jszip-library-with-known-vulnerabilities generic %}
To fix this issue, you just need to update JSZip to the latest version available on their [website](https://stuk.github.io/jszip/).

Do not forget to update all the JSZip files you have on the server.
{% endtab %}

{% endtabs %}
