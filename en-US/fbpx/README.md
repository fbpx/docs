---
title: FBPX
---

FBPX is the main command line program for Chiχ​.


The following commands are available:

- [login](/docs/fbpx/login)
- [run](/docs/fbpx/run)
- [graph](/docs/fbpx/graph)
- [input](/docs/fbpx/input)
- [deps](/docs/fbpx/deps)
- [tokens](/docs/fbpx/tokens)
- [list/info](/docs/fbpx/list)
- [convert](/docs/fbpx/convert)
- [compile](/docs/fbpx/compile)
- [install](/docs/fbpx/install)
- [browserify](/docs/fbpx/browserify)
- [deploy](/docs/fbpx/deploy)


```
 fbpx --help

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
    login                             Login to api.chix.io to set token
    deps [options]                    Show dependencies
    deploy                            Deploy nodes to api.
    tokens [options]                  Debug lexer tokens
    list|info [options]               List available nodes
    compile [options]                 Compile nodes
    convert|c [options]               Convert file
    install|i [options]               Load node definitions & install requirements
    browserify|brsf [options] [file]  Create a browserified bundle
```
