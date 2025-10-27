---
name: Inclusion of cryptocurrency mining script
severity: high
cvss-score: 7.1
cvss-vector: CVSS:3.1/AV:N/AC:L/PR:N/UI:R/S:C/C:L/I:L/A:L
cwe-id: CWE-830
cwe-name: Inclusion of Web Functionality from an Untrusted Source
compliance:
  HIPAA: 164.306(a), 164.312(c)(1)
  owasp10: A8
  PCI-DSS v4.0.1: 6.2.4

---            

Your application is including a JavaScript library known to abuse the computing resources of the victim's computer to mine cryptocurrencies. 

The presence of this type of libraries is usually a strong indicator that your application has been compromised (which allowed the attacker to add the malicious content).

Clients connecting to your web application will turn into victims while this malicious JavaScript uses their computing power, making the device slower. Clients will notice their CPU going to 100% when visiting your site, affecting your application reputation. In addition, your web application may be marked as malicious and be blocked by security controls, such as those present in modern browsers, preventing your customers from reaching the site.

## How to fix

{% tabs inclusion-of-cryptocurrency-mining-script %}
{% tab inclusion-of-cryptocurrency-mining-script generic %}
Stop including the malicious JavaScript library in the site by deleting all references to it. 

Please note that your web application may have been hacked through another vulnerability that allowed the attacker to insert this library. It's also possible, but less likely, that an employee with access to the code/server may have changed the application for his/her own profit.
{% endtab %}

{% endtabs %}
