---
name: Install
---

# Install

Installs the dependencies of a flow file.

Prior to installation make sure the current directory (or one of it's ancestors) contains a `package.json`.


### Usage

Create a package json if it does not exist yet.
```
$ npm init -y
```

Example flow containing a node which uses a dependency (In this case superagent)
```
title: Example flow

provider https://api.chix.io/v1/nodes/rhalff/{ns}/{name}

Request(superagent/get)

'http://example.com' -> url Request

Request request -> request EndRequest
Request body -> msg Log(console/log)
```


```
$ fbpx install example.fbp
+ superagent@3.8.3
added 24 packages from 22 contributors and audited 25 packages in 2.168s
found 0 vulnerabilities
```