---
name: Graph
---

# Graph

Generates a dot graph from your flow file.

Usage:
```
 fbpx graph test.fbp
digraph structs {
  label="Example flow!";

  node [shape=record];

  xRequest [shape="record", label="{{<INPUT_url>url}|Request|{<OUTPUT_request>request}}",comment=""];
  xEndRequest [shape="record", label="{{<INPUT_request>request}|EndRequest|{<OUTPUT_res>res}}",comment=""];
  xLog [shape="record", label="{{<INPUT_msg>msg}|Log}",comment=""];

  xRequest:OUTPUT_request -> xEndRequest:INPUT_request;
  xEndRequest:OUTPUT_res -> xLog:INPUT_msg;

  xIIP0 [shape="plaintext",label="'http://example.com/'",comment=""];
  xIIP0 -> xRequest:INPUT_url;

}
```

This output can then be used to generate an .svg, .png etc. using a tool which is able to read dot graphs.

e.g.
```
fbpx graph test.fbp | dot -Tpng > test.png
```

Which will result in the diagram below:

![Test.png](https://repos.chix.io/chix/docs/raw/8c53f03b89f36ba9cff2f6284d40096f3e1a56ab/en-US/fbpx/test.svg)