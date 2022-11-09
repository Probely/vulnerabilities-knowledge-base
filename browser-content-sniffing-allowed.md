---
name: Browser content sniffing allowed
severity: low
cvss-score: 4.7
cvss-vector: CVSS:3.0/AV:N/AC:H/PR:N/UI:R/S:C/C:L/I:L/A:N
cwe-id: CWE-16
cwe-name: Configuration
compliance:
  owasp10: A5

---            

The application allows browsers to try to mime-sniff the content-type of the responses. This means the browser may try to guess the content-type by looking at the response content, and render it in way it was not intended to. This behavior may lead to the execution of malicious code, for instance, to explore an XSS vulnerability.

Applications should disable this behavior, forcing browsers to honor the content-type specified in the response. Without a specific content-type set browsers will default to render the content as text, turning XSS payloads innocuous.

Disabling mime-sniffing should be seen as an extra layer of defense against XSS, and not as replacement of the recommended XSS prevention techniques.

## How to fix

{% tabs browser-content-sniffing-allowed %}
{% tab browser-content-sniffing-allowed generic %}
This problem can be fixed by sending the header **X-Content-Type-Options** with value **nosniff**, to force browsers to disable the content-type guessing (the sniffing).

The header should look this:

	X-Content-Type-Options: nosniff

It is normally easy to enable the header in the web server configuration file, but it can also be done at application level.
{% endtab %}

{% tab browser-content-sniffing-allowed nginx %}
This problem can be fixed by sending the header **X-Content-Type-Options** with value **nosniff**, to force browsers to disable the content-type guessing (the sniffing).

The header should look this:

	X-Content-Type-Options: nosniff

For nginx add the following line to your virtual host configuration file:

	add_header X-Content-Type-Options "nosniff" always;

It is normally easy to enable the header in the web server configuration file, but it can also be done at application level.
{% endtab %}

{% tab browser-content-sniffing-allowed apache %}
This problem can be fixed by sending the header **X-Content-Type-Options** with value **nosniff**, to force browsers to disable the content-type guessing (the sniffing).

The header should look this:

	X-Content-Type-Options: nosniff

For Apache add the following line to your virtual host configuration file:

	Header always set X-Content-Type-Options "nosniff"

It is usually easy to enable the header in the web server configuration file, but it can also be done at application level.
{% endtab %}

{% endtabs %}
