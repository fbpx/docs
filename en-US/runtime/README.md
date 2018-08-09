---
name: Runtime
---

# Chix Runtime

Runtime to be used with the noflo fbp protocol:

http://noflojs.org/documentation/protocol/

Installation:

```
npm install
```

Test:
```
npm test
```

Usage:
```
 Usage: fbpx-server [options] <file ...>

  Options:

    -h, --help              output usage information
    -V, --version           output the version number
    -t, --type [name]       Runtime type chix, noflo-nodejs
    -c, --cache             cache components
    -p, --proxy             expose /proxy to proxy requests to e.g. a browser
    -s, --secure            secure wss or ws
    -u, --uppercase         force ports uppercase
    -h, --host [name]       hostname
    -p, --port [name]       port
    -I, --no-ids            do not use uuids
    -b, --bail              bail on errors
    -i, --interface [name]  choose a webserver interface
    -l, --loader [loader]   loader `remote` or `npm`
    -L, --loglevel [level]  Log level
    -f, --flowhub           ping flowhub
    -v, --verbose           verbose output
```

# Transport

The transport will be independent from the protocol itself.

It's job is:

  - receiving
  - sending
  - keep track of client scope.

For the noflo protocol, the scope are graphs.

# Monitors

The monitors will listen for output from whatever it listen to.
They only know how to sendAll(), sendAll is a negotiating method within
the transport. This method will determine who is concidered to be `all`.
This will mainly depend on what is considered the scope parameter.

# Handlers

Handlers will handle the received requests. Sometimes they will need to send
data back to the requester, sometimes they will not send any data back.

The requester will then receive it's reply as part of the group who is `subscribed` to the
particular scope. Which is a graph in the context of this protocol.

# Implementation of the above.

There are three variants for now:

  - receive
  - receive / send
  - sendAll

The schema defines when a property is considered to be a topic.
In this case, `graph` will always be defined as topic.

This can then be used within the transport to categorize the clients.
sendAll will then be aware of who it is it must send its reply to.

## Flowhub

To run the chix-runtime and be able to use the UI at https://app.flowhub.com

You must first register.

```
npm run register
```

Above will generate a flowhub.json file, you must modify this file
to contain your flowhub userID

In order to connect with flowhub the server must be started in secure mode.
A simple way to do this is to run the script `create_cert.sh'

After this you must run the server in secure mode:
```
fbpx-server main_graph.fbp --flowhub --secure -L debug
```

### HTTPS

First generate a certificate.

If the connection is not trusted, first go to the url with a browser
and accept the self signed certificate, otherwise the connection
will silently fail with a 500 message.

### Schemas

To update the modified yaml schemas run:
```
npm run schemas
```
This will update ./schemas.js in the root directory

