
# Table of contents

- [Table of contents](#table-of-contents)
- [Methods](#methods)
  - [`.is(type: Object) -> Logic`](#istype-object---logic)
  - [`.isAny(...types: List<Object>) -> Object | Nil`](#isanytypes-listobject---object--nil)
- [Operators](#operators)
  - [`.add(right: String) -> String`](#addright-string---string)

# Methods

## `.is(type: Object) -> Logic`

Returns whether the value is of the specified type or not.

```lxm
any.is(type)
```

### Parameters

- **`type`**: the type object to check against.

### Errors

- **`BadArgumentError`**: when the `type` argument is not a type object.

### Examples

```lxm
let object = true

object.is(Logic)    -- true
object.is(List)     -- false
```

## `.isAny(...types: List<Object>) -> Object | Nil`

Checks whether the value is of one of the specified types, returning the type or not, returning `nil`.

```lxm
any.isAny(type1, ..., typeN)
```

### Parameters

- **`types`**: the list of type objects to check against.

### Errors

- **`BadArgumentError`**: when any of the `types` are not a type object.

### Examples

```lxm
let object = true

object.isAny(Logic, List)   -- Logic
object.isAny(Object, List)  -- nil
```

# Operators

## `.add(right: String) -> String`

Returns the concatenation of the string representation of `this` value and the `right` value, i.e `this.toString() + right`.

```lxm
any.add(right)
```

### Parameters

- **`right`**: the right operand.

### Errors

- **`BadArgumentError`**: when the type of `right` is incorrect.

### Examples

```lxm
let left = 7
let right = " kingdoms"

log(left.add(right))    -- "7 kingdoms"
log(left.add(nil))      -- BadArgumentError
log(left + right)       -- "7 kingdoms" Implicit calling
```
