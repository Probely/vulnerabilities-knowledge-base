This problem can be fixed by sending the header **X-Content-Type-Options** with value **nosniff**, to force browsers to disable the content-type guessing (the sniffing).

The header should look this:

	X-Content-Type-Options: nosniff

For nginx add the following line to your virtual host configuration file:

	add_header X-Content-Type-Options "nosniff" always;

It is normally easy to enable the header in the web server configuration file, but it can also be done at application level.