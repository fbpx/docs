---
name: Getting Started
---

# Getting Started

Let's create our first Chiχ project!

After you've install the fbpx cli, you can test it by writing your first .fbp file.

Open a blank file with an .fbp extension. e.g. `hello_world.fbp`

```
provider ./{ns}.{name}.yml

'Hello World!' -> msg Log(console/log)
```

Save the file and close it.

We have now defined a flow which will receive a `Hello World!` message on it's `msg` port.

The provider is mandatory and specifies how to resolve the nodes we are using within our flow definition.

Before running it we can inspect the flow to see what we have defined:
```
$ fbpx convert hello_world.fbp --yaml
type: flow
nodes:
  - id: Log
    title: Log
    ns: console
    name: log
links: []
providers:
  '@':
    path: './{ns}.{name}.yml'

```

We have defined one node and do not have any links yet.
The `@` indicates the default provider for this flow file is `{ns}.{name}.yml`

The input we have defined in the flow definition is not present, this is by intention.
You can verify whether the input is actually detected by running:
```
 $ fbpx input hello_world.fbp 

 Input Data

┌────────────────┬──────┬─────────┐
│ Data           │ Port │ Process │
├────────────────┼──────┼─────────┤
│ "Hello World!" │ msg  │ Log     │
└────────────────┴──────┴─────────┘
```

So now try running the flow:
```
$ fbpx run hello_world.fbp 
ENOENT: no such file or directory, open './console.log.yml'
```

This is kind of expected, we have specified how to resolve the nodes, but did not create a node definition file yet.

So let's create it:
console.log.yml
```
title: My Console Log Node
ns: console
name: log
ports:
  input:
    in:
      type: string
fn: "console.log($.in)"
```
The `ns` and `name` pair are mandatory and must match what was specified in the provider uri.

The ports describe what input we expect.

`fn` contains the function body of which the contains will be evaluated.

Having created our node definition, the flow can now be executed.

```
$ 
```