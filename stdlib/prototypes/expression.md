
# Table of contents

- [Table of contents](#table-of-contents)
- [Methods](#methods)
  - [`.wrap(...arguments: List<Any>, ...namedArguments: Object) -> Function`](#wraparguments-listany-namedarguments-object---function)

# Methods

## `.wrap(...arguments: List<Any>, ...namedArguments: Object) -> Function`

Returns a new `Function` that when invoked it will call the current function with the specified arguments (`arguments` and `namedArguments`).

```lxm
expression.wrap(thisValue, argument1, ..., argumentN, namedArgument1 = value, ..., namedArgumentN = value)
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Expression`.

### Examples

```lxm
exp test(a, b) {
    Debug.log("a: ", a)
    Debug.log("b: ", b)
    Debug.log("this: ", this)
}

val wrapper = test.wrap("I'm a", b = "I'm b", this = "I'm this")

wrapper()

-- Output:
-- a: I'm a
-- b: I'm b
-- this: I'm this
```
