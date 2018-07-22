# Node



# Node Functions
There are several ways of defining to functionality within the node.


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

