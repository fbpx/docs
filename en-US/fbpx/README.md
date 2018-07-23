---
name: FBPX
---

# FBPX

FBPX is the main command line program for Chiχ​.

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