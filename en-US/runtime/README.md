---
title: FBPX Runtime
---

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


