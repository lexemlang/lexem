
# Table of contents

- [Table of contents](#table-of-contents)
- [Methods](#methods)
  - [`.parameters() -> Objects`](#parameters---objects)
  - [`.wrap(...arguments: List<Any>, ...namedArguments: Object) -> Function`](#wraparguments-listany-namedarguments-object---function)

# Methods

## `.parameters() -> Objects`

Returns an `Object` that contains the names of the parameters of the function.

```lxm
function.parameters()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Function`.

### Examples

```lxm
fun test(a, b, c, ...d, ...@e) {}

log(num.parameters())  -- #{params: set!["a", "b", "c"], spread: "d", namedSpread: "e"}
```

## `.wrap(...arguments: List<Any>, ...namedArguments: Object) -> Function`

Returns a new `Function` that when invoked it will call the current function with the specified arguments (`arguments` and `namedArguments`).

```lxm
function.wrap(thisValue, argument1, ..., argumentN, namedArgument1 = value, ..., namedArgumentN = value)
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Function`.

### Examples

```lxm
fun test(a, b) {
    log("a: ", a)
    log("b: ", b)
    log("this: ", this)
}

val wrapper = test.wrap("I'm a", b = "I'm b", this = "I'm this")

wrapper()

-- Output:
-- a: I'm a
-- b: I'm b
-- this: I'm this
```
