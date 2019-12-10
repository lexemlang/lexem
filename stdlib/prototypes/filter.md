
# Table of contents

- [Table of contents](#table-of-contents)
- [Methods](#methods)
  - [.wrap(...arguments: List&lt;Any&gt;, ...namedArguments: Object) -&gt; Function](#wraparguments-listltanygt-namedarguments-object--gt-function)

# Methods

## `.wrap(...arguments: List<Any>, ...namedArguments: Object) -> Function`

Returns a new `Function` that when invoked it will call the current function with the specified arguments (`arguments` and `namedArguments`).

```lxm
filter.wrap(thisValue, argument1, ..., argumentN, namedArgument1 = value, ..., namedArgumentN = value)
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Filter`.

### Examples

```lxm
filter test(a, b) {
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
