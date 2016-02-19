# Getting req.protocol with express, nodejs and nginx

You are on https with ssl termination at your proxy and the `req.protocol` you see is `http`, instead of `https`? This is a correct behavior by default.

As per the [behind proxy documentation](http://expressjs.com/en/guide/behind-proxies.html), you need to set the `trust proxy` configuration enabled (or to a set of IP addresses) if you want to have `X-Forwarded-*` headers to be part of the entries that express would use.

On your expressjs side, you need to have the following after initiating express app:
```javascript
var express = require("express");
var app = express();
app.enable("trust proxy");
```

As per the documentation, the client’s IP address is understood as the left-most entry in the X-Forwarded-* header if we enable the `trust proxy`.

On the nginx side, you need to make sure your location block that contains `proxy_pass` has `X-Forwarded-Proto` set.

```
location / {
    proxy_pass       http://techgaun_proxy/;
    proxy_set_header   Connection "";
    proxy_http_version 1.1;
    proxy_set_header        Host            $host;
    proxy_set_header        X-Real-IP       $remote_addr;
    proxy_set_header        X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_set_header X-Forwarded-Proto $scheme;
}
```

Now, you should be able to get appropriate `req.protocol` in your express app.
