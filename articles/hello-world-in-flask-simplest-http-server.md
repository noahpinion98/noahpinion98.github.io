---
layout: default
title: Hello World in Flask: simplest HTTP server
description: A minimal Flask example showing the fastest way to start a local HTTP server and serve static index.html.
permalink: /articles/hello-world-in-flask-simplest-http-server
---

This is the easiest way to start an HTTP server with Flask.

Example repo: [noahpinion98/flask-static-example](https://github.com/noahpinion98/flask-static-example)

```python
#!/usr/bin/env python3

from flask import Flask, send_from_directory

app = Flask(__name__)


@app.route("/")
def home_page():
    return send_from_directory("static", "index.html")


if __name__ == "__main__":
    app.run()
```

Run it, open `http://127.0.0.1:5000`, and you have a working local HTTP server serving `static/index.html`.
