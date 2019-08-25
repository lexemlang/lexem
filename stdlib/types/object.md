
# Table of contents

- [Table of contents](#table-of-contents)
- [Methods](#methods)
  - [`.newFrom(prototype: Object) -> Object`](#newfromprototype-object---object)
    - [Parameters](#parameters)
    - [Errors](#errors)
    - [Examples](#examples)
  - [`.assign(target: Object, ...sources: List<Object>) -> Object`](#assigntarget-object-sources-listobject---object)
    - [Parameters](#parameters-1)
    - [Errors](#errors-1)
    - [Examples](#examples-1)
- [Properties](#properties)
  - [`.prototype -> Object`](#prototype---object)

# Methods

## `.newFrom(prototype: Object) -> Object`

Returns a new empty `Object` with the given object as prototype.

```lxm
Object.newFrom(prototype)
```

### Parameters

- **`prototype`**: the object that will act as the prototype of the new object.

### Errors

- **`BadArgumentError`**: when the type of `prototype` is not an `Object`.

### Examples

```lxm
let prototype = {b: "prototype"}
let currentObj = Object.newFrom(prototype)
currentObj.a = "current"

log(currentObj)     -- {a: "current"}
log(currentObj.b)   -- "prototype"
```

## `.assign(target: Object, ...sources: List<Object>) -> Object`

Returns the target object with all the properties of the source objects assigned to it.

```lxm
Object.assign(target, source1, ..., sourceN)
```

### Parameters

- **`target`**: the target object that will hold all properties.
- **`sources`**: the source objects that will be assigned to the target.

### Errors

- **`BadArgumentError`**: when any of these conditions do not math.
  - the type of `target` is not an `Object`.
  - the type of any source object is not `Object`.

### Examples

```lxm
let target = {a: 1, b: 2}
let source1 = {b: 3, c: 4}
let source2 = {c: 5, d: 6}

Object.assign(target, source1, source2)

log(target)     -- {a: 1, b: 3, c: 5, d: 6}
log(source1)    -- {b: 3, c: 4}
log(source2)    -- {c: 5, d: 6}
```

# Properties

## `.prototype -> Object`

The prototype of the type.

```lxm
Object.prototype
```
