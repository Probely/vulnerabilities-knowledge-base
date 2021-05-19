This problem can be fixed by sending the header **X-Content-Type-Options** with value **nosniff**, to force browsers to disable the content-type guessing (the sniffing).

The header should look this:

	X-Content-Type-Options: nosniff

For Apache add the following line to your virtual host configuration file:

	Header always set X-Content-Type-Options "nosniff"

It is usually easy to enable the header in the web server configuration file, but it can also be done at application level.