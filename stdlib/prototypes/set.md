
# Table of contents

- [Table of contents](#table-of-contents)
- [Methods](#methods)
  - [`.size()`](#size)
  - [`.freeze()`](#freeze)
  - [`.isFrozen() -> Logic`](#isfrozen---logic)
  - [`.every(fn: Function) -> Logic`](#everyfn-function---logic)
  - [`.filter(fn: Function) -> Set`](#filterfn-function---set)
  - [`.forEach(fn: Function)`](#foreachfn-function)
  - [`.find(fn: Function) -> Any | Nil`](#findfn-function---any-nil)
  - [`.containsAny(...values: List<Any>) -> Logic`](#containsanyvalues-listany---logic)
  - [`.containsAll(...values: List<Any>) -> Logic`](#containsallvalues-listany---logic)
  - [`.map(fn: Function) -> Set`](#mapfn-function---set)
  - [`.reduce(default: Any, fn: Function) -> Any`](#reducedefault-any-fn-function---any)
  - [`.any(fn: Function) -> Logic`](#anyfn-function---logic)
  - [`.add(...values: List<Any>)`](#addvalues-listany)
  - [`.remove(...values: List<Any>)`](#removevalues-listany)
  - [`.toList() -> List`](#tolist---list)
  - [`.toString() -> String`](#tostring---string)
- [Operators](#operators)
  - [`.add(right: Set) -> Set`](#addright-set---set)
  - [`.sub(right: Set) -> Set`](#subright-set---set)
  - [`.logicAnd(right: Set) -> Set`](#logicandright-set---set)
  - [`.logicOr(right: Set) -> Set`](#logicorright-set---set)
  - [`.logicXor(right: Set) -> Set`](#logicxorright-set---set)

# Methods

## `.size()`

Returns the number of elements in the current set.

```lxm
set.size()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Set`.

### Examples

```lxm
let set = set![1, 2, 3]

log(set.size())   -- 3
```

## `.freeze()`

Makes the set constant so it can't be extended, shrinked or modified.

```lxm
set.freeze()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Set`.

### Examples

```lxm
let set = set![]

set.freeze()

log(set)        -- set!#[]
```

## `.isFrozen() -> Logic`

Whether the set is constant or not.

```lxm
set.isFrozen()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Set`.

### Examples

```lxm
let set = set!#[]

log(set.isFrozen())     -- true
```

## `.every(fn: Function) -> Logic`

Returns `true` if `fn` returns a truthy value for every element in the set, otherwise returns `false`.

```lxm
set.every(fn)
```

### Parameters

- **`fn`**: the function to execute once per value in the set.

### Errors

- **`BadArgumentError`**: when the type of `fn` is not a `Function`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Set`.

### Examples

```lxm
let set = set![1, 2, 3]

fun gt0(value) { return value > 0 }
fun gt2(value) { return value > 2 }

log(set.every(gt0)) -- true
log(set.every(gt2)) -- false
```

## `.filter(fn: Function) -> Set`

Returns a new set with only the values for which `fn` returns a truthy value.

```lxm
set.filter(fn)
```

### Parameters

- **`fn`**: the function to execute once per value in the set.

### Errors

- **`BadArgumentError`**: when the type of `fn` is not a `Function`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Set`.

### Examples

```lxm
let set = set![1, 2, 3]

fun gt2(value) { return value > 2 }
fun falseFn(value) { return false }

log(set.filter(gt2))     -- set![3]
log(set.filter(falseFn)) -- set![]
```

## `.forEach(fn: Function)`

Executes a function once per element in the current set.

```lxm
set.forEach(fn)
```

### Parameters

- **`fn`**: the function to execute once per value in the set.

### Errors

- **`BadArgumentError`**: when the type of `fn` is not a `Function`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Set`.

### Examples

```lxm
let set = set![1, 2, 3]

var count = 0
fun add(value) { count + value }

set.forEach(add)

log(count)    -- 6
```

## `.find(fn: Function) -> Any | Nil`

Returns the first element for which `fn` returns a truthy value or `nil` otherwise.

```lxm
set.find(fn)
```

### Parameters

- **`fn`**: the function to execute once per value in the set.

### Errors

- **`BadArgumentError`**: when the type of `fn` is not a `Function`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Set`.

### Examples

```lxm
let set = set![1, 2, 3]

fun gt1(value) { return value > 1 }
fun gt5(value) { return value > 5 }

log(set.find(gt1))  -- 2
log(set.find(gt5))  -- nil
```

## `.containsAny(...values: List<Any>) -> Logic`

Returns a `Logic` value indicating whether any of the values are present in the current set. The function returns `false` if there is no values.

```lxm
set.containsAny(value1, ..., valueN)
```

### Parameters

- **`values`**: all the values to check.

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Set`.

### Examples

```lxm
let set = set![1, 2, 3]

log(set.containsAny(1, 7, 9))   -- true
log(set.containsAny(-4, 5))     -- false
log(set.containsAny())          -- false
```

## `.containsAll(...values: List<Any>) -> Logic`

Returns a `Logic` value indicating whether all the the values are present in the current set. The function returns `true` if there is no values.

```lxm
set.containsAll(value1, ..., valueN)
```

### Parameters

- **`values`**: all the values to check.

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Set`.

### Examples

```lxm
let set = set![1, 2, 3]

log(set.containsAll(1, 3))    -- true
log(set.containsAll(1, 5))    -- false
log(set.containsAll())        -- true
```

## `.map(fn: Function) -> Set`

Returns a new `Set` filled with the values returned by `fn` fo each value.

```lxm
set.map(fn)
```

### Parameters

- **`fn`**: the function to execute once per value in the set.

### Errors

- **`BadArgumentError`**: when the type of `fn` is not a `Function`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Set`.

### Examples

```lxm
let set = set![1, 2, 3]

fun add10(value) { return value + 10 }

log(set.map(add10))   -- set![11, 12, 13]
```

## `.reduce(default: Any, fn: Function) -> Any`

Returns the accumulated value of processing with `fn` all values of the current set.

```lxm
set.reduce(default, fn)
```

### Parameters

- **`default`**: the default value to accumulate the result.
- **`fn`**: the function to execute once per value in the set.

### Errors

- **`BadArgumentError`**: when the type of `fn` is not a `Function`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Set`.

### Examples

```lxm
let set = set![1, 2, 3]

fun add(accumulation, value) { return accumulation + value }

log(set.reduce(0, add))     -- 6
log(set.reduce(10, add))    -- 16
```

## `.any(fn: Function) -> Logic`

Returns `true` if `fn` returns a truthy value for any of the elements in the set, otherwise returns `false`.

```lxm
set.any(fn)
```

### Parameters

- **`fn`**: the function to execute once per value in the set.

### Errors

- **`BadArgumentError`**: when the type of `fn` is not a `Function`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Set`.

### Examples

```lxm
let set = set![1, 2, 3]

fun gt2(value) { return value > 2 }
fun gt5(value) { return value > 5 }

log(set.any(gt2)) -- true
log(set.any(gt5)) -- false
```

## `.add(...values: List<Any>)`

Add new values to the current set.

```lxm
set.add(value1, ..., valueN)
```

### Parameters

- **`values`**: all the values to add.

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Set`.

### Examples

```lxm
let set = set![1, 2, 3]

set.add(1, 5)
log(set)    -- set![1, 2, 3, 5]

set.add()
log(set)    -- set![1, 2, 3, 5]
```

## `.remove(...values: List<Any>)`

Remove some values from the current set.

```lxm
set.remove(value1, ..., valueN)
```

### Parameters

- **`values`**: all the values to remove.

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Set`.

### Examples

```lxm
let set = set![1, 2, 3]

set.remove(1, 5)
log(set)    -- set![2, 3]

set.remove()
log(set)    -- set![2, 3]
```

## `.toList() -> List`

Transforms the current set into a `List`. The order is not guaranteed.

```lxm
set.toList()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Set`.

### Examples

```lxm
let set = set![1, 2, 3]

log(set.toList())    -- [1, 2, 3]
```

## `.toString() -> String`

Return the `String` representation of the current set.

```lxm
set.toString()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Set`.

### Examples

```lxm
let set = set![1, 2, 3]

log(set.toString())    -- "set![1, 2, 3]"
```

# Operators

## `.add(right: Set) -> Set`

Returns a new `Set` with the values in both sets.

```lxm
set.add(right)
```

### Parameters

- **`right`**: the right operand.

### Errors

- **`BadArgumentError`**: when the type of `right` is incorrect.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Set`.

### Examples

```lxm
let left = set![1, 2, 3, 4, 5]
let right = set![2, 4, 6, 8]

log(left.add(right))        -- set![1, 2, 3, 4, 5, 6, 8]
log(left.add(nil))          -- BadArgumentError
log(left + right)           -- set![1, 2, 3, 4, 5, 6, 8] Implicit calling
```

## `.sub(right: Set) -> Set`

Returns a new `Set` with the values of the current set removing the values of the `right` set.

```lxm
set.sub(right)
```

### Parameters

- **`right`**: the right operand.

### Errors

- **`BadArgumentError`**: when the type of `right` is incorrect.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Set`.

### Examples

```lxm
let left = set![1, 2, 3, 4, 5]
let right = set![2, 4, 6, 8]

log(left.sub(right))    -- set![1, 3, 5]
log(left.sub(nil))      -- BadArgumentError
log(left - right)       -- set![1, 3, 5] Implicit calling
```

## `.logicAnd(right: Set) -> Set`

Returns a new `Set` with those values that are set in both sets at the same time.

```lxm
set.logicAnd(right)
```

### Parameters

- **`right`**: the right operand.

### Errors

- **`BadArgumentError`**: when the type of `right` is incorrect.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Set`.

### Examples

```lxm
let left = set![1, 2, 3, 4, 5]
let right = set![2, 4, 6, 8]

log(left.logicAnd(right))   -- set![2, 4]
log(left.logicAnd(nil))     -- BadArgumentError
log(left & right)           -- set![2, 4] Implicit calling
```

## `.logicOr(right: Set) -> Set`

Returns a new `Set` with the values in both sets.

```lxm
set.logicOr(right)
```

### Parameters

- **`right`**: the right operand.

### Errors

- **`BadArgumentError`**: when the type of `right` is incorrect.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Set`.

### Examples

```lxm
let left = set![1, 2, 3, 4, 5]
let right = set![2, 4, 6, 8]

log(left.logicOr(right))    -- set![1, 2, 3, 4, 5, 6, 8]
log(left.logicOr(nil))      -- BadArgumentError
log(left | right)           -- set![1, 2, 3, 4, 5, 6, 8] Implicit calling
```

## `.logicXor(right: Set) -> Set`

Returns a new `Set` with those values that just set in one of both sets.

```lxm
set.logicXor(right)
```

### Parameters

- **`right`**: the right operand.

### Errors

- **`BadArgumentError`**: when the type of `right` is incorrect.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Set`.

### Examples

```lxm
let left = set![1, 2, 3, 4, 5]
let right = set![2, 4, 6, 8]

log(left.logicXor(right))   -- set![1, 3, 5, 6, 8]
log(left.logicXor(nil))     -- BadArgumentError
log(left ^ right)           -- set![1, 3, 5, 6, 8] Implicit calling
```
