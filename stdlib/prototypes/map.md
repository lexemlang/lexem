
# Table of contents

- [Table of contents](#table-of-contents)
- [Methods](#methods)
  - [.size() -&gt; Integer](#size--gt-integer)
  - [.freeze() -&gt; Nil](#freeze--gt-nil)
  - [.isFrozen() -&gt; Logic](#isfrozen--gt-logic)
  - [.every(fn: Function) -&gt; Logic](#everyfn-function--gt-logic)
  - [.filter(fn: Function) -&gt; Map](#filterfn-function--gt-map)
  - [.forEach(fn: Function) -&gt; Nil](#foreachfn-function--gt-nil)
  - [.containsAnyKey(...values: List&lt;Any&gt;) -&gt; Logic](#containsanykeyvalues-listltanygt--gt-logic)
  - [.containsAllKeys(...values: List&lt;Any&gt;) -&gt; Logic](#containsallkeysvalues-listltanygt--gt-logic)
  - [.map(fn: Function) -&gt; Map](#mapfn-function--gt-map)
  - [.reduce(default: Any, fn: Function) -&gt; Any](#reducedefault-any-fn-function--gt-any)
  - [.any(fn: Function) -&gt; Logic](#anyfn-function--gt-logic)
  - [.put(key: Any, value: Any) -&gt; Nil](#putkey-any-value-any--gt-nil)
  - [.remove(...keys: List&lt;Any&gt;) -&gt; Nil](#removekeys-listltanygt--gt-nil)
  - [.toList() -&gt; List](#tolist--gt-list)
  - [.toObject() -&gt; Object](#toobject--gt-object)
  - [.keys() -&gt; List](#keys--gt-list)
  - [.values() -&gt; List](#values--gt-list)
  - [.toString() -&gt; String](#tostring--gt-string)
  - [.clear() -&gt; Nil](#clear--gt-nil)
- [Operators](#operators)
  - [.add(right: Map) -&gt; Map](#addright-map--gt-map)
  - [.sub(right: Map) -&gt; Map](#subright-map--gt-map)
  - [.logicAnd(right: Map) -&gt; Map](#logicandright-map--gt-map)
  - [.logicOr(right: Map) -&gt; Map](#logicorright-map--gt-map)
  - [.logicXor(right: Map) -&gt; Map](#logicxorright-map--gt-map)
- [Accesses](#accesses)
  - [[key: Any] -&gt; Any](#key-any--gt-any)
  - [[key: Any] = value: Any -&gt; Any](#key-any--value-any--gt-any)

# Methods

## `.size() -> Integer`

Returns the number of elements in the current map.

```lxm
map.size()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Map`.

### Examples

```lxm
let map = [1, 2, 3]

Debug.log(map.size())    -- 3
```

## `.freeze() -> Nil`

Makes the map constant so it can't be extended, shrank or modified.

```lxm
map.freeze()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Map`.

### Examples

```lxm
let map = {}

map.freeze()

Debug.log(map)     -- #{}
```

## `.isFrozen() -> Logic`

Whether the map is constant or not.

```lxm
map.isFrozen()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Map`.

### Examples

```lxm
let map = #{}

Debug.log(map.isFrozen())  -- true
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

Debug.log(map.every(gt0))    -- true
Debug.log(map.every(gt2))    -- false
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

Debug.log(map.filter(gt1))       -- map!{"b": 2}
Debug.log(map.filter(falseFn))   -- map!{}
```

## `.forEach(fn: Function) -> Nil`

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

Debug.log(count)    -- 3
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

Debug.log(map.containsAnyKey("a", "c"))   -- true
Debug.log(map.containsAnyKey("d"))        -- false
Debug.log(map.containsAnyKey())           -- false
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

Debug.log(map.containsAllKeys("a", "b"))  -- true
Debug.log(map.containsAllKeys("a", "c"))  -- false
Debug.log(map.containsAllKeys())          -- true
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

Debug.log(map.map(add10))   -- [11, 12, 13]
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

Debug.log(map.reduce(0, add))     -- 3
Debug.log(map.reduce(10, add))    -- 13
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

Debug.log(map.any(gt1)) -- true
Debug.log(map.any(gt5)) -- false
```

## `.put(key: Any, value: Any) -> Nil`

Adds a key-value in the current map.

```lxm
map.put(key, value)
```

### Parameters

- **`key`**: the key to add.
- **`value`**: the value of the key.

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Map`.

### Examples

```lxm
let map = map!{"a": 1, "b": 2}

map.put("a", 5)
Debug.log(list)   -- map!{"a": 5, "b": 2}
å
map.put(5, 6)
Debug.log(list)   -- map!{"a": 1, "b": 2, 5: 6}
```

## `.remove(...keys: List<Any>) -> Nil`

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
Debug.log(list)   -- map!{"b": 2}

map.remove()
Debug.log(list)   -- map!{"b": 2}
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

Debug.log(map.toList())   -- [{key: "a", value: 1}, {key: "b", value: 2}]
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

Debug.log(map.toObject())   -- {a: 1, b: 2}
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

Debug.log(map.keys())   -- ["a", "b"]
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

Debug.log(map.values())   -- [1, 2]
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

Debug.log(map.toString())    -- "map!{\"a\": 1, \"b\": 2}"
```

## `.clear() -> Nil`

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

Debug.log(map)    -- map!{}
```

# Operators

## `.add(right: Map) -> Map`

Returns a new `Map` with the values in both sets. The values of `right` have more precedence when keys are present in both.

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

Debug.log(left.add(right))        -- map!{1: "a", "b": 5, true: 4,5}
Debug.log(left.add(nil))          -- BadArgumentError
Debug.log(left + right)           -- map!{1: "a", "b": 5, true: 4,5} Implicit calling
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

Debug.log(left.sub(right))    -- map!{1: "a"}
Debug.log(left.sub(nil))      -- BadArgumentError
Debug.log(left - right)       -- map!{1: "a"} Implicit calling
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

Debug.log(left.logicAnd(right))   -- map!{"b": 5}
Debug.log(left.logicAnd(nil))     -- BadArgumentError
Debug.log(left & right)           -- map!{"b": 5} Implicit calling
```

## `.logicOr(right: Map) -> Map`

Returns a new `Map` with the values in both sets. The values of `right` has more precedence when keys are present in both.

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

Debug.log(left.logicOr(right))    -- map!{1: "a", "b": 5, true: 4,5}
Debug.log(left.logicOr(nil))      -- BadArgumentError
Debug.log(left | right)           -- map!{1: "a", "b": 5, true: 4,5} Implicit calling
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

Debug.log(left.logicXor(right))   -- map!{1: "a", true: 4.5}
Debug.log(left.logicXor(nil))     -- BadArgumentError
Debug.log(left ^ right)           -- map!{1: "a", true: 4.5} Implicit calling
```

# Accesses

## `[key: Any] -> Any`

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

Debug.log(map[nil])   -- nil
Debug.log(map[1])     -- "a"
Debug.log(map[2])     -- 4
```

## `[key: Any] = value: Any -> Any`

Assigns `value` to `key` and returns `value`. If the key does not exist. it is added.

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

Debug.log(map[nil])   -- nil
Debug.log(map[1])     -- "a"
Debug.log(map[2])     -- 4

map[1] = 3      -- map = map!{1: 3, 2: 4}
map[3] = 4      -- map = map!{1: 3, 2: 4, 3: 4}
```
