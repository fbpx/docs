---
name: Node
---

# Node



# Node Functions
There are several ways of defining to functionality within the node.

These functions are very convenient in many cases, they are however also limited.
If orchestration between ports becomes important, you should use the class variant.

e.g. if the node will only require some settings and one main input port, the function type is convenient.

The function runs, executes and is ready for the next call.


### Just the function body

This is this easiest form, you assign the port output to the `output` variable.

```
output = {
  in: $.create('My Result')
}
```

### output as a function

```
output = () => {

  cb({
    out: $.create('My Result')
  })
}
```

### Port Boxes

```
on.input.in = () => {
  output({
    out: $.create('My Result')
  })
}
```

These port functions can also be defined within the port definition itself, e.g.
```
ports:
  input:
    in:
      type: string
      fn: |
        output({
          out: $.create('My Result')
        })
```

