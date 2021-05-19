This problem is caused because the application sends the header **X-XSS-Protection** with value **0**, so can either stop sending the header or changing it to **1**.

By default, browsers have the XSS protection enabled, therefore not sending the header at all will keep the XSS filter enabled.
Sending the header with **1** will enable the protection, if not already. For nginx add the following line to your virtual host configuration file:

	add_header X-XSS-Protection "1" always;

Additionally there is one optional directive for this header: **mode=block**.   

	add_header X-XSS-Protection "1; mode=block" always;

This directive instructs the browser to stop rendering the page if a malicious payload is detected in URL, instead of sanitizing the URL by removing the malicious parts, which is the default behavior. Blocking rendering is safer, since it prevents side effects caused by sanitization.