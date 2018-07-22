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
    msg:
      type: string
fn: "console.log($.msg)"
```
The `ns` and `name` pair are mandatory and must match what was specified in the provider uri.

The ports describe what input we expect.

`fn` contains the function body of which the contains will be evaluated.

The '$' namespace contains the `Packet` api and gives access to the current input data. 
In this case we directly refer to the contents of packet arriving at the `msg` port and log it's contents.

Having created our node definition, the flow can now be executed.

```bash
$ fbpx run hello_world.fbp 
Hello World!
```

### Creating Links

In order to create something more interesting let's add some more nodes.

Chiχ is all about utilizing the fast amount of javascript packages already available on the internet.

It's main concept is not to write code, but utilizing existing functionality and wrapping it in such a way the packages can be composed into graphs.

So let's pick an interesting package from npm. e.g. https://www.npmjs.com/package/say
Instead of just logging `Hello World!` it would be nice to actually hear it.

In order to use packages, we first must execute `npm init -y` inside our project directory.
```
$ npm init -y
```

As `fbpx` will expect it to be present and store the dependencies.

We can either directly install the package through npm or use `fbpx install hello_world.fbp' to install all dependencies used by the nodes defined in the flow file.

Created a new file following our provider's resolve pattern (`./{ns}.{name}.yml`). To contain our `Say.js` node definition.

console.say.yml
```
title: Say.js
ns: console
name: say
ports:
  input:
    msg:
      type: string
dependencies:
  npm:
    say: 'latest'
fn: 'say.speak($.msg)'
```

We now have declared a dependencies of the type 'npm'.
All dependencies will be available by their name, and converted to an underscored string if necessary.

Having defined our say component, let's add it to our flow definition:
```
provider ./{ns}.{name}.yml

'Hello World!' -> msg SayIt(console/say)

```



