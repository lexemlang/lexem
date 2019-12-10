
# Table of contents

- [Table of contents](#table-of-contents)
- [Methods](#methods)
  - [.assign(target: Map, ...sources: List&lt;Map&gt;) -&gt; Map](#assigntarget-map-sources-listltmapgt--gt-map)
- [Properties](#properties)
  - [.prototype -&gt; Object](#prototype--gt-object)

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

Debug.log(target)     -- map!{a: 1, b: 3, c: 5, d: 6}
Debug.log(source1)    -- map!{b: 3, c: 4}
Debug.log(source2)    -- map!{c: 5, d: 6}
```

# Properties

## `.prototype -> Object`

The prototype of the type.

```lxm
Map.prototype
```
