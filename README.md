# fastuaparser
A super-fast user agent string parser


## Usage

```py
from fastuaparser import parse_ua

# Parse the user agent header to get a descriptive string.
# (This never raises an exception).
client_os = parse_ua(headers.get("user-agent", ""))

# Want to process browser-type and OS seperately?
client, os = client_os.partition(' - ')
```


## A bit less precise, a whole lot faster

This code is less precise than https://github.com/ua-parser/uap-python,
in that it marks rare browsers as either "Browser" or as the browser
that it's based upon (e.g. IceWeasel becomes Firefox). It also marks
all bots as simply "Bot" and does not care about TV's that have a
browser. Other than that, this function is quite accurate and passes
ua-parser's test suite.

If you can live with the above restrictions (you probably can if
you're using this to e.g. monitor your website's traffic) then use
this function: it's over 100 times faster that ua_parser!

Efficiency matters. It means you can do analytics on your web server
without adding significant overhead. These little savings of CPU add
up, and can help reduce the carbon footprint of your web server.


## Origins

This code used to be part of [my time tracking app](https://timeturtle.app),
but now I'm moving things around, and turning it into a open source
package is just easier.


## License

MIT
