
# Table of contents

- [Table of contents](#table-of-contents)
- [Methods](#methods)
  - [`.toString() -> String`](#tostring---string)

# Methods

## `.toString() -> String`

Returns a `String` representing the logic value.

```lxm
logic.toString()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Nil`.

### Examples

```lxm
let value = nil

log(value.toString())   -- "nil"
```
