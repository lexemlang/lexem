
# Table of contents

- [Table of contents](#table-of-contents)
- [Methods](#methods)
  - [`.size()`](#size)
    - [Errors](#errors)
    - [Examples](#examples)
  - [`.every(fn: Function) -> Logic`](#everyfn-function---logic)
    - [Parameters](#parameters)
    - [Errors](#errors-1)
    - [Examples](#examples-1)
  - [`.filter(fn: Function) -> Map`](#filterfn-function---map)
    - [Parameters](#parameters-1)
    - [Errors](#errors-2)
    - [Examples](#examples-2)
  - [`.forEach(fn: Function)`](#foreachfn-function)
    - [Parameters](#parameters-2)
    - [Errors](#errors-3)
    - [Examples](#examples-3)
  - [`.containsAnyKey(...values: List<Any>) -> Logic`](#containsanykeyvalues-listany---logic)
    - [Parameters](#parameters-3)
    - [Errors](#errors-4)
    - [Examples](#examples-4)
  - [`.containsAllKeys(...values: List<Any>) -> Logic`](#containsallkeysvalues-listany---logic)
    - [Parameters](#parameters-4)
    - [Errors](#errors-5)
    - [Examples](#examples-5)
  - [`.map(fn: Function) -> Map`](#mapfn-function---map)
    - [Parameters](#parameters-5)
    - [Errors](#errors-6)
    - [Examples](#examples-6)
  - [`.reduce(default: Any, fn: Function) -> Any`](#reducedefault-any-fn-function---any)
    - [Parameters](#parameters-6)
    - [Errors](#errors-7)
    - [Examples](#examples-7)
  - [`.any(fn: Function) -> Logic`](#anyfn-function---logic)
    - [Parameters](#parameters-7)
    - [Errors](#errors-8)
    - [Examples](#examples-8)
  - [`.add(key: Any, value: Any)`](#addkey-any-value-any)
    - [Parameters](#parameters-8)
    - [Errors](#errors-9)
    - [Examples](#examples-9)
  - [`.remove(...keys: List<Any>)`](#removekeys-listany)
    - [Parameters](#parameters-9)
    - [Errors](#errors-10)
    - [Examples](#examples-10)
  - [`.toList() -> List`](#tolist---list)
    - [Errors](#errors-11)
    - [Examples](#examples-11)
  - [`.toObject() -> Object`](#toobject---object)
    - [Errors](#errors-12)
    - [Examples](#examples-12)
  - [`.keys() -> List`](#keys---list)
    - [Errors](#errors-13)
    - [Examples](#examples-13)
  - [`.values() -> List`](#values---list)
    - [Errors](#errors-14)
    - [Examples](#examples-14)
  - [`.toString() -> String`](#tostring---string)
    - [Errors](#errors-15)
    - [Examples](#examples-15)
  - [`.clear()`](#clear)
    - [Errors](#errors-16)
    - [Examples](#examples-16)
- [Operators](#operators)
  - [`.add(right: Map) -> Map`](#addright-map---map)
    - [Parameters](#parameters-10)
    - [Errors](#errors-17)
    - [Examples](#examples-17)
  - [`.sub(right: Map) -> Map`](#subright-map---map)
    - [Parameters](#parameters-11)
    - [Errors](#errors-18)
    - [Examples](#examples-18)
  - [`.logicAnd(right: Map) -> Map`](#logicandright-map---map)
    - [Parameters](#parameters-12)
    - [Errors](#errors-19)
    - [Examples](#examples-19)
  - [`.logicOr(right: Map) -> Map`](#logicorright-map---map)
    - [Parameters](#parameters-13)
    - [Errors](#errors-20)
    - [Examples](#examples-20)
  - [`.logicXor(right: Map) -> Map`](#logicxorright-map---map)
    - [Parameters](#parameters-14)
    - [Errors](#errors-21)
    - [Examples](#examples-21)
- [Accesses](#accesses)
  - [`.index(key: Any) -> Any`](#indexkey-any---any)
    - [Parameters](#parameters-15)
    - [Errors](#errors-22)
    - [Examples](#examples-22)
  - [`.index(key: Any, value: Any) -> Any`](#indexkey-any-value-any---any)
    - [Parameters](#parameters-16)
    - [Errors](#errors-23)
    - [Examples](#examples-23)

# Methods

## `.size()`

Returns the number of elements in the current map.

```lxm
map.size()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Map`.

### Examples

```lxm
let map = [1, 2, 3]

log(map.size())    -- 3
```

## `.every(fn: Function) -> Logic`

Returns `true` if `fn` returns a truthy value for every element in the map, otherwise returns `false`.

```lxm
map.every(fn)
```

### Parameters

- **`fn`**: the function to execute once per value in the map.

### Errors

- **`BadArgumentError`**: when the type of `fn` is not a `Function`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Map`.

### Examples

```lxm
let map = map!{"a": 1, "b": 2}

fun gt0(value, key) { return value > 0 }
fun gt2(value, key) { return value > 2 }

log(map.every(gt0))    -- true
log(map.every(gt2))    -- false
```

## `.filter(fn: Function) -> Map`

Returns a new map with only the values for which `fn` returns a truthy value.

```lxm
map.filter(fn)
```

### Parameters

- **`fn`**: the function to execute once per value in the map.

### Errors

- **`BadArgumentError`**: when the type of `fn` is not a `Function`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Map`.

### Examples

```lxm
let map = map!{"a": 1, "b": 2}

fun gt1(value, key) { return value > 1 }
fun falseFn(value, key) { return false }

log(map.filter(gt1))       -- map!{"b": 2}
log(map.filter(falseFn))   -- map!{}
```

## `.forEach(fn: Function)`

Executes a function once per element in the current map.

```lxm
map.forEach(fn)
```

### Parameters

- **`fn`**: the function to execute once per value in the map.

### Errors

- **`BadArgumentError`**: when the type of `fn` is not a `Function`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Map`.

### Examples

```lxm
let map = map!{"a": 1, "b": 2}

var count = 0
fun add(value, key) { count + value }

map.forEach(add)

log(count)    -- 3
```

## `.containsAnyKey(...values: List<Any>) -> Logic`

Returns a `Logic` value indicating whether any of the values are present in the current map. The function returns `false` if there is no values.

```lxm
map.containsAnyKey(value1, ..., valueN)
```

### Parameters

- **`values`**: all the values to check.

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Map`.

### Examples

```lxm
let map = map!{"a": 1, "b": 2}

log(map.containsAnyKey("a", "c"))   -- true
log(map.containsAnyKey("d"))        -- false
log(map.containsAnyKey())           -- false
```

## `.containsAllKeys(...values: List<Any>) -> Logic`

Returns a `Logic` value indicating whether all the the values are present in the current map. The function returns `true` if there is no values.

```lxm
map.containsAllKeys(value1, ..., valueN)
```

### Parameters

- **`values`**: all the values to check.

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Map`.

### Examples

```lxm
let map = map!{"a": 1, "b": 2}

log(map.containsAllKeys("a", "b"))  -- true
log(map.containsAllKeys("a", "c"))  -- false
log(map.containsAllKeys())          -- true
```

## `.map(fn: Function) -> Map`

Returns a new `Map` filled with the values returned by `fn` fo each value.

```lxm
map.map(fn)
```

### Parameters

- **`fn`**: the function to execute once per value in the map.

### Errors

- **`BadArgumentError`**: when the type of `fn` is not a `Function`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Map`.

### Examples

```lxm
let map = map!{"a": 1, "b": 2}

fun add10(value, key) { return value + 10 }

log(map.map(add10))   -- [11, 12, 13]
```

## `.reduce(default: Any, fn: Function) -> Any`

Returns the accumulated value of processing with `fn` all values of the current map.

```lxm
map.reduce(default, fn)
```

### Parameters

- **`default`**: the default value to accumulate the result.
- **`fn`**: the function to execute once per value in the map.

### Errors

- **`BadArgumentError`**: when the type of `fn` is not a `Function`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Map`.

### Examples

```lxm
let map = map!{"a": 1, "b": 2}

fun add(accumulation, value, key) { return accumulation + value }

log(map.reduce(0, add))     -- 3
log(map.reduce(10, add))    -- 13
```

## `.any(fn: Function) -> Logic`

Returns `true` if `fn` returns a truthy value for any of the elements in the map, otherwise returns `false`.

```lxm
map.any(fn)
```

### Parameters

- **`fn`**: the function to execute once per value in the map.

### Errors

- **`BadArgumentError`**: when the type of `fn` is not a `Function`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Map`.

### Examples

```lxm
let map = map!{"a": 1, "b": 2}

fun gt1(value, key) { return value > 1 }
fun gt5(value, key) { return value > 5 }

log(map.any(gt1)) -- true
log(map.any(gt5)) -- false
```

## `.add(key: Any, value: Any)`

Adds a key-value in the current map.

```lxm
map.remove(key, value)
```

### Parameters

- **`key`**: the key to add.
- **`value`**: the value of the key.

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Map`.

### Examples

```lxm
let map = map!{"a": 1, "b": 2}

map.add("a", 5)
log(list)   -- map!{"a": 5, "b": 2}
å
map.add(5, 6)
log(list)   -- map!{"a": 1, "b": 2, 5: 6}
```

## `.remove(...keys: List<Any>)`

Remove some keys from the current map.

```lxm
map.remove(value1, ..., valueN)
```

### Parameters

- **`keys`**: all the keys to remove.

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Map`.

### Examples

```lxm
let map = map!{"a": 1, "b": 2}

map.remove("a")
log(list)   -- map!{"b": 2}

map.remove()
log(list)   -- map!{"b": 2}
```

## `.toList() -> List`

Transforms the current map into a `List`. The order is not guaranteed.

```lxm
map.toList()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Map`.

### Examples

```lxm
let map = map!{"a": 1, "b": 2}

log(map.toList())   -- [{key: "a", value: 1}, {key: "b", value: 2}]
```

## `.toObject() -> Object`

Transforms the current map into an `Object` mapping the keys of type `String`.

```lxm
map.toObject()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Map`.

### Examples

```lxm
let map = map!{"a": 1, "b": 2, true: 3, 5: 6}

log(map.toObject())   -- {a: 1, b: 2}
```

## `.keys() -> List`

Returns a list with all the keys of the map. The order is not guaranteed.

```lxm
map.keys()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Map`.

### Examples

```lxm
let map = map!{"a": 1, "b": 2}

log(map.keys())   -- ["a", "b"]
```

## `.values() -> List`

Returns a list with all the values of the map. The order is not guaranteed.

```lxm
map.values()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Map`.

### Examples

```lxm
let map = map!{"a": 1, "b": 2}

log(map.values())   -- [1, 2]
```

## `.toString() -> String`

Return the `String` representation of the current map.

```lxm
map.toString()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Map`.

### Examples

```lxm
let map = map!{"a": 1, "b": 2}

log(map.toString())    -- "map!{\"a\": 1, \"b\": 2}"
```

## `.clear()`

Removes all elements from the map.

```lxm
map.clear()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Map`.

### Examples

```lxm
let map = map!{"a": 1, "b": 2}

map.clear()

log(map)    -- map!{}
```

# Operators

## `.add(right: Map) -> Map`

Returns a new `Map` with the values in both sets. The values of `right` has precedence when keys are present in both.

```lxm
map.add(right)
```

### Parameters

- **`right`**: the right operand.

### Errors

- **`BadArgumentError`**: when the type of `right` is incorrect.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Map`.

### Examples

```lxm
let left = map!{1: "a", "b": 2}
let right = map!{"b": 5, true: 4.5}

log(left.add(right))        -- map!{1: "a", "b": 5, true: 4,5}
log(left.add(nil))          -- BadArgumentError
log(left + right)           -- map!{1: "a", "b": 5, true: 4,5} Implicit calling
```

## `.sub(right: Map) -> Map`

Returns a new `Map` with the values of the current set removing the values of the `right` map.

```lxm
map.sub(right)
```

### Parameters

- **`right`**: the right operand.

### Errors

- **`BadArgumentError`**: when the type of `right` is incorrect.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Map`.

### Examples

```lxm
let left = map!{1: "a", "b": 2}
let right = map!{"b": 5, true: 4.5}

log(left.sub(right))    -- map!{1: "a"}
log(left.sub(nil))      -- BadArgumentError
log(left - right)       -- map!{1: "a"} Implicit calling
```

## `.logicAnd(right: Map) -> Map`

Returns a new `Map` with those values that are set in both sets at the same time. The values of `right` have precedence.

```lxm
map.logicAnd(right)
```

### Parameters

- **`right`**: the right operand.

### Errors

- **`BadArgumentError`**: when the type of `right` is incorrect.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Map`.

### Examples

```lxm
let left = map!{1: "a", "b": 2}
let right = map!{"b": 5, true: 4.5}

log(left.logicAnd(right))   -- map!{"b": 5}
log(left.logicAnd(nil))     -- BadArgumentError
log(left & right)           -- map!{"b": 5} Implicit calling
```

## `.logicOr(right: Map) -> Map`

Returns a new `Map` with the values in both sets. The values of `right` has precedence when keys are present in both.

```lxm
map.logicOr(right)
```

### Parameters

- **`right`**: the right operand.

### Errors

- **`BadArgumentError`**: when the type of `right` is incorrect.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Map`.

### Examples

```lxm
let left = map!{1: "a", "b": 2}
let right = map!{"b": 5, true: 4.5}

log(left.logicOr(right))    -- map!{1: "a", "b": 5, true: 4,5}
log(left.logicOr(nil))      -- BadArgumentError
log(left | right)           -- map!{1: "a", "b": 5, true: 4,5} Implicit calling
```

## `.logicXor(right: Map) -> Map`

Returns a new `Map` with those values that just set in one of both maps.

```lxm
map.logicXor(right)
```

### Parameters

- **`right`**: the right operand.

### Errors

- **`BadArgumentError`**: when the type of `right` is incorrect.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Map`.

### Examples

```lxm
let left = map!{1: "a", "b": 2}
let right = map!{"b": 5, true: 4.5}

log(left.logicXor(right))   -- map!{1: "a", true: 4.5}
log(left.logicXor(nil))     -- BadArgumentError
log(left ^ right)           -- map!{1: "a", true: 4.5} Implicit calling
```

# Accesses

## `.index(key: Any) -> Any`

Returns the value of the `key` or `nil` if the key does not exist.

```lxm
map[index]
```

### Parameters

- **`key`**: the key to access.

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Map`.

### Examples

```lxm
let map = map!{1: "a", 2: 4}

log(map[nil])   -- nil
log(map[1])     -- "a"
log(map[2])     -- 4
```

## `.index(key: Any, value: Any) -> Any`

Assigns `value` to `key` and returns `value`. If the kye does not exist. it is added.

```lxm
map[key] = value
```

### Parameters

- **`key`**: the key to access.

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Map`.

### Examples

```lxm
let map = map!{1: "a", 2: 4}

log(map[nil])   -- nil
log(map[1])     -- "a"
log(map[2])     -- 4

map[1] = 3      -- map = map!{1: 3, 2: 4}
map[3] = 4      -- map = map!{1: 3, 2: 4, 3: 4}
```
