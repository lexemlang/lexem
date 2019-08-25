
# Table of contents

- [Table of contents](#table-of-contents)
- [Methods](#methods)
  - [`.assign(target: Map, ...sources: List<Map>) -> Map`](#assigntarget-map-sources-listmap---map)
    - [Parameters](#parameters)
    - [Errors](#errors)
    - [Examples](#examples)
- [Properties](#properties)
  - [`.prototype -> Object`](#prototype---object)

# Methods

## `.assign(target: Map, ...sources: List<Map>) -> Map`

Returns the target map with all the properties of the source maps assigned to it.

```lxm
Map.assign(target, source1, ..., sourceN)
```

### Parameters

- **`target`**: the target map that will hold all properties.
- **`sources`**: the source maps that will be assigned to the target.

### Errors

- **`BadArgumentError`**: when any of these conditions do not math.
  - the type of `target` is not a `Map`.
  - the type of any source object is not `Map`.

### Examples

```lxm
let target = map!{a: 1, b: 2}
let source1 = map!{b: 3, c: 4}
let source2 = map!{c: 5, d: 6}

Map.assign(target, source1, source2)

log(target)     -- map!{a: 1, b: 3, c: 5, d: 6}
log(source1)    -- map!{b: 3, c: 4}
log(source2)    -- map!{c: 5, d: 6}
```

# Properties

## `.prototype -> Object`

The prototype of the type.

```lxm
Map.prototype
```
