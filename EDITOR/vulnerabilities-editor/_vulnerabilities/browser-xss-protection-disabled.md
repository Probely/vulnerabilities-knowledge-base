---
name: Browser XSS protection disabled
severity: low
cvss-score: 1
cvss-vector: CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:L/I:N/A:N
cwe-id: cwe-1337
cwe-name: Browser XSS protection disabled
alias: ["alias1", "alias2", "alias3"]
compliance:
  owasp10: none
---

This problem is caused because the application sends the header **X-XSS-Protection** with value **0**, so can either stop sending the header or changing it to **1**.

By default, browsers have the XSS protection enabled, therefore not sending the header at all will keep the XSS filter enabled.
Sending the header with **1** will enable the protection, if not already.

{% tabs log %}
{% tab log nginx %}
This problem is caused because the application sends the header **X-XSS-Protection** with value **0**, so can either stop sending the header or changing it to **1**.

By default, browsers have the XSS protection enabled, therefore not sending the header at all will keep the XSS filter enabled.
Sending the header with **1** will enable the protection, if not already. For nginx add the following line to your virtual host configuration file:

```nginx
	add_header X-XSS-Protection "1" always;
```

Additionally there is one optional directive for this header: **mode=block**.

```nginx
	add_header X-XSS-Protection "1; mode=block" always;
```

This directive instructs the browser to stop rendering the page if a malicious payload is detected in URL, instead of sanitizing the URL by removing the malicious parts, which is the default behavior. Blocking rendering is safer, since it prevents side effects caused by sanitization.
{% endtab %}

{% tab log apache %}
This problem is caused because the application sends the header **X-XSS-Protection** with value **0**, so can either stop sending the header or changing it to **1**.

By default, browsers have the XSS protection enabled, therefore not sending the header at all will keep the XSS filter enabled.
Sending the header with **1** will enable the protection, if not already. For Apache add the following line to your virtual host configuration file:

```apache
	Header always set X-XSS-Protection "1"
```

Additionally there is one optional directive for this header: **mode=block**.

```apache
	Header always set X-XSS-Protection "1; mode=block"
```

This directive instructs the browser to stop rendering the page if a malicious payload is detected in URL, instead of sanitizing the URL by removing the malicious parts, which is the default behavior. Blocking rendering is safer, since it prevents side effects caused by sanitization.
{% endtab %}

{% endtabs %}
