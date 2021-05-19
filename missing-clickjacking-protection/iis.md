The recommended way to prevent clickjacking is to send a header that instructs the browser to not allow arbitrary framing, typically from other domains.

The current recommendation is to use the Content-Security-Policy HTTP header (CSP) with a **frame-ancestors** directive. This header obsoletes the X-Frame-Options HTTP header.

To use CSP you need the following header:

	Content-Security-Policy: frame-ancestors 'none'

The header might contain more directives, and there are other less strict options for the **frame-ancestors** directive.


If you want to use X-Frame-Options, send the proper HTTP header, with one of the following directives:

	X-Frame-Options: DENY  
	X-Frame-Options: SAMEORIGIN

A third directive, **ALLOW-FROM** is no longer supported by modern browsers. 

If you specify **DENY**, all attempts to load the page in a frame will fail. **SAMEORIGIN** will allow the page to be loaded in the site including it in a frame is the same as the one serving the page. 

The most common option is **DENY** when there is no need to load your pages on some other site.

<br>

To configure IIS to send the Content-Security-Policy header, add this your site's Web.config file:

	<system.webServer>
	  ...
	
	  <httpProtocol>
	    <customHeaders>
	      <add name="Content-Security-Policy" value="frame-ancestors 'none'" />
	    </customHeaders>
	  </httpProtocol>
	
	  ...
	</system.webServer>


To configure IIS to send the X-Frame-Options header, add this your site's Web.config file:

	<system.webServer>
	  ...
	
	  <httpProtocol>
	    <customHeaders>
	      <add name="X-Frame-Options" value="DENY" />
	    </customHeaders>
	  </httpProtocol>
	
	  ...
	</system.webServer>