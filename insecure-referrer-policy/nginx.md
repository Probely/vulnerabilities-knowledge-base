This problem can be fixed by sending the header **Referrer-Policy** with a secure value.
There are different values available, but not all are considered secure. The following list explains each one, and it is ordered from the safest to the least safe:

* `no-referrer`: never send the header.
* `same-origin`: send the full URL to requests to the same origin (exact scheme + domain)
* `strict-origin`: send only the domain part of the URL, but sends nothing when downgrading to HTTP.
* `origin`: similar to **strict-origin** without downgrade restriction.
* `strict-origin-when-cross-origin`: send full URL within the same origin, but only the domain part when sending to another origin. It sends nothing when downgrading to HTTP.
* `origin-when-cross-origin`: similar to **strict-origin-when-cross-origin** without the downgrade restriction.

Insecure options:
* `no-referrer-when-downgrade`: sends the full URL when the scheme does not change. It will send if both origins are, for instance, HTTP.
* `unsafe-url`: always sent the full URL

A possible, safe option is `strict-origin`, so for nginx add the following line to your virtual host configuration file:

	add_header Referrer-Policy "strict-origin" always;

It is normally easy to enable the header in the web server configuration file, but it can also be done at the application level.


Please note that the referrer header is written `referer`, with a single `r` but the referrer policy header is properly written, with `rr`: `Referrer-Policy`.