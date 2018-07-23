---
name: Run
---

# Run

Run the graph.

example.fbp
```
title: Example flow

provider https://api.chix.io/v1/nodes/rhalff/{ns}/{name}

Request(superagent/api)
EndRequest(superagent/end)

'http://example.com' -> url Request

Request request -> request EndRequest
EndRequest res [text] -> msg Log(console/log
```


```
$ fbpx run test.fbp
<!doctype html>
<html>
<head>
    <title>Example Domain</title>
    ...
```

Using debug, you'll see a lot of debugging information:
```
$ DEBUG=* fbpx run test.fbp
```

Under the hood `chix-flow` is using the [debug](https://www.npmjs.com/package/debug) package.
Which makes it possible to select what kind of debug messages you want to see.

Currently the following namespaces are available:

- chix:io
- chix:inputPort
- chix:connector
- chix:pm
- chix:packet
- chix:actor
- chix:node
- chix:outputPort

