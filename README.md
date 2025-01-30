# fastuaparser
A super-fast user-agent string parser


## Usage

```py
from fastuaparser import parse_ua

# Parse the header info
client_os = parse_ua(headers.get("user-agent", ""))

# Split in browser-type and OS
client, os = client_os.partition(' - ')
```

The `parse_ua()` function never raises an exception, just tries
to make as much from whatever you feed it.


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


## Origins

This code used to be part of [my time tracking app](https://timetagger.app),
which went open source, and I rolled some components (like this one) into
their own little project.


## License

MIT
