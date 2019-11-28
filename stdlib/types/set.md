
# Table of contents

- [Table of contents](#table-of-contents)
- [Methods](#methods)
  - [`.newFrom(...values: List<Any>) -> Set`](#newfromvalues-listany---set)
  - [`.join(...sets: List<Set>) -> Set`](#joinsets-listset---set)
- [Properties](#properties)
  - [`.prototype -> Object`](#prototype---object)

# Methods

## `.newFrom(...values: List<Any>) -> Set`

Returns a new `Set` containing all the specified values.

```lxm
Set.newFrom(value1, ..., valueN)
```

### Parameters

- **`values`**: the initial values of the set.

### Examples

```lxm
Debug.log(Set.newFrom(3, false, 3))  -- set![3, false]
```

## `.join(...sets: List<Set>) -> Set`

Returns a new `Set` containing all the values of each of the specified sets.

```lxm
Set.join(set1, ..., setN)
```

### Parameters

- **`sets`**: the sets to join.

### Errors

- **`BadArgumentError`**: when any set is not a `Set`.

### Examples

```lxm
Debug.log(Set.join(set![2, 3.5], set![true, "test"]))     -- set![2, 3.5, true, "test"]
```

# Properties

## `.prototype -> Object`

The prototype of the type.

```lxm
Set.prototype
```
