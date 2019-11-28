
# Table of contents

- [Table of contents](#table-of-contents)
- [Methods](#methods)
  - [`.new(size: Integer, value: Any) -> List`](#newsize-integer-value-any---list)
  - [`.newFrom(...values: List<Any>) -> List`](#newfromvalues-listany---list)
  - [`.concat(...lists: List<List>) -> List`](#concatlists-listlist---list)
- [Properties](#properties)
  - [`.prototype -> Object`](#prototype---object)

# Methods

## `.new(size: Integer, value: Any) -> List`

Returns a new `List` with the specified size and initial value.

```lxm
List.new(size, value)
```

### Parameters

- **`size`**: the initial size of the list.
- **`value`**: the initial value for all cells in the list.

### Errors

- **`BadArgumentError`**: when the type of `size` is not an `Integer` or is lower than 0.

### Examples

```lxm
Debug.log(List.new(2, 44))        -- [44, 44]
Debug.log(List.new(3, false))     -- [false, false, false]
```

## `.newFrom(...values: List<Any>) -> List`

Returns a new `List` containing all the specified values.

```lxm
List.newFrom(value1, ..., valueN)
```

### Parameters

- **`values`**: the initial values of the list.

### Examples

```lxm
Debug.log(List.newFrom(3, false))     -- [3, false]
```

## `.concat(...lists: List<List>) -> List`

Returns a new `List` containing all the values of each of the specified lists.

```lxm
List.concat(list1, ..., listN)
```

### Parameters

- **`lists`**: the lists to concat.

### Errors

- **`BadArgumentError`**: when any list is not a `List`.

### Examples

```lxm
Debug.log(List.concat([2, 3.5], [true, "test"]))    -- [2, 3.5, true, "test"]
```

# Properties

## `.prototype -> Object`

The prototype of the type.

```lxm
List.prototype
```
