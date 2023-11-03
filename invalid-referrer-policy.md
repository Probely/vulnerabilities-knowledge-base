---
name: Invalid referrer policy
severity: low
cvss-score: 3.1
cvss-vector: CVSS:3.0/AV:N/AC:H/PR:N/UI:R/S:U/C:L/I:N/A:N
cwe-id: CWE-200
cwe-name: Exposure of Sensitive Information to an Unauthorized Actor
compliance:
  ISO 27001: A.8.9
  owasp10: A2, A5

---            

The application does not prevent browsers from sending sensitive information to third party sites in the **referer** header, because your **Referrer-Policy** header is invalid.

Without a valid referrer policy, every time a user clicks a link that takes him to another origin (domain), the browser will add a **referer** header with the URL from which he is coming from. That URL may contain sensitive information, such as password recovery tokens or personal information, and it will be visible that other origin. For instance, if the user is at `example.com/password_recovery?unique_token=14f748d89d` and clicks a link to `example-analytics.com`, that origin will receive the complete password recovery URL in the headers and might be able to set the users password.
The same happens for requests made automatically by the application, such as XHR ones.

Applications should set a secure referrer policy that prevents sensitive data from being sent to third party sites.

## How to fix

{% tabs invalid-referrer-policy %}
{% tab invalid-referrer-policy generic %}
This problem can be fixed by sending the header **Referrer-Policy** with a secure and valid value.
There are different values available, but not all are considered secure. Please note that this header only supports one directive at a time. The following list explains each one and it is ordered from the safest to the least safe:

* `no-referrer`: never send the header.
* `same-origin`: send the full URL to requests to the same origin (exact scheme + domain)
* `strict-origin`: send only the domain part of the URL, but sends nothing when downgrading to HTTP.
* `origin`: similar to **strict-origin** without downgrade restriction.
* `strict-origin-when-cross-origin`: send full URL within the same origin, but only the domain part when sending to another origin. It sends nothing when downgrading to HTTP.
* `origin-when-cross-origin`: similar to **strict-origin-when-cross-origin** without the downgrade restriction.

Insecure options:
* `no-referrer-when-downgrade`: sends the full URL when the scheme does not change. It will send if both origins are, for instance, HTTP.
* `unsafe-url`: always sent the full URL

A possible, safe option is `strict-origin`, so the header would look like this:

	Referrer-Policy: strict-origin

It is normally easy to enable the header in the web server configuration file, but it can also be done at the application level.


Please note that the referrer header is written `referer`, with a single `r` but the referrer policy header is properly written, with `rr`: `Referrer-Policy`.
{% endtab %}

{% endtabs %}
