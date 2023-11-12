---
title: Installation
---

The main command line tool for Chiχ is `fbpx`, you can install it using npm.


```
$ npm i @fbpx/cli -g
```

```
$ fbpx --help

  Usage: fbpx [options] [file ...]

  Options:

    -V, --version                     output the version number
    -v, --verbose                     verbose output
    -C, --nocache                     do not read/write cache
    -P, --purge                       purge cache file
    -l, --log [level]                 log [level]
    -h, --help                        output usage information

  Commands:

    run|r [options] [filename]        Run graph
    graph|g [options] [filename]      Show Graph
    input [options]                   Show input data
    login                             Login to api.fbpx.io to set token
    deps [options]                    Show dependencies
    deploy                            Deploy nodes to api.
    tokens [options]                  Debug lexer tokens
    list|info [options]               List available nodes
    compile [options]                 Compile nodes
    convert|c [options]               Convert file
    install|i [options]               Load node definitions & install requirements
    browserify|brsf [options] [file]  Create a browserified bundle
```
