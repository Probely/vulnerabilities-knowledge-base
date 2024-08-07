---
name: Chart.js library with known vulnerabilities
severity: low
cvss-score: 4.8
cvss-vector: CVSS:3.0/AV:N/AC:H/PR:N/UI:N/S:U/C:L/I:L/A:N
cwe-id: CWE-1035
cwe-name: OWASP Top Ten 2017 Category A9 - Using Components with Known Vulnerabilities
compliance:
  HIPAA: 164.306(a)
  ISO 27001: A.8.9
  owasp10: A5, A6
  pci: '6.2'
  PCI v4.0: pci4-6.2.4, pci4-6.3.3

---            

The application uses an outdated version of the Chart.js library, which has known vulnerabilities.

## How to fix

{% tabs chartjs-library-with-known-vulnerabilities %}
{% tab chartjs-library-with-known-vulnerabilities generic %}
To fix this issue, you just need to update Chart.js to the latest version available on their [website](https://www.chartjs.org/).

Do not forget to update all the Chart.js files you have on the server.
{% endtab %}

{% endtabs %}
