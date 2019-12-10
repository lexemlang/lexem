
# Table of contents

- [Table of contents](#table-of-contents)
- [Methods](#methods)
  - [.size() -&gt; Integer](#size--gt-integer)
  - [.freeze() -&gt; Nil](#freeze--gt-nil)
  - [.isFrozen() -&gt; Logic](#isfrozen--gt-logic)
  - [.every(fn: Function) -&gt; Logic](#everyfn-function--gt-logic)
  - [.filter(fn: Function) -&gt; Set](#filterfn-function--gt-set)
  - [.forEach(fn: Function) -&gt; Nil](#foreachfn-function--gt-nil)
  - [.find(fn: Function) -&gt; Any | Nil](#findfn-function--gt-any-nil)
  - [.containsAny(...values: List&lt;Any&gt;) -&gt; Logic](#containsanyvalues-listltanygt--gt-logic)
  - [.containsAll(...values: List&lt;Any&gt;) -&gt; Logic](#containsallvalues-listltanygt--gt-logic)
  - [.map(fn: Function) -&gt; Set](#mapfn-function--gt-set)
  - [.reduce(default: Any, fn: Function) -&gt; Any](#reducedefault-any-fn-function--gt-any)
  - [.any(fn: Function) -&gt; Logic](#anyfn-function--gt-logic)
  - [.put(...values: List&lt;Any&gt;) -&gt; Nil](#putvalues-listltanygt--gt-nil)
  - [.remove(...values: List&lt;Any&gt;) -&gt; Nil](#removevalues-listltanygt--gt-nil)
  - [.toList() -&gt; List](#tolist--gt-list)
  - [.toString() -&gt; String](#tostring--gt-string)
  - [.clear() -&gt; Nil](#clear--gt-nil)
- [Operators](#operators)
  - [.add(right: Set) -&gt; Set](#addright-set--gt-set)
  - [.sub(right: Set) -&gt; Set](#subright-set--gt-set)
  - [.logicAnd(right: Set) -&gt; Set](#logicandright-set--gt-set)
  - [.logicOr(right: Set) -&gt; Set](#logicorright-set--gt-set)
  - [.logicXor(right: Set) -&gt; Set](#logicxorright-set--gt-set)

# Methods

## `.size() -> Integer`

Returns the number of elements in the current set.

```lxm
set.size()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Set`.

### Examples

```lxm
let set = set![1, 2, 3]

Debug.log(set.size())   -- 3
```

## `.freeze() -> Nil`

Makes the set constant so it can't be extended, shrank or modified.

```lxm
set.freeze()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Set`.

### Examples

```lxm
let set = set![]

set.freeze()

Debug.log(set)        -- set!#[]
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

Debug.log(set.isFrozen())     -- true
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

Debug.log(set.every(gt0)) -- true
Debug.log(set.every(gt2)) -- false
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

Debug.log(set.filter(gt2))     -- set![3]
Debug.log(set.filter(falseFn)) -- set![]
```

## `.forEach(fn: Function) -> Nil`

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

Debug.log(count)    -- 6
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

Debug.log(set.find(gt1))  -- 2
Debug.log(set.find(gt5))  -- nil
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

Debug.log(set.containsAny(1, 7, 9))   -- true
Debug.log(set.containsAny(-4, 5))     -- false
Debug.log(set.containsAny())          -- false
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

Debug.log(set.containsAll(1, 3))    -- true
Debug.log(set.containsAll(1, 5))    -- false
Debug.log(set.containsAll())        -- true
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

Debug.log(set.map(add10))   -- set![11, 12, 13]
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

Debug.log(set.reduce(0, add))     -- 6
Debug.log(set.reduce(10, add))    -- 16
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

Debug.log(set.any(gt2)) -- true
Debug.log(set.any(gt5)) -- false
```

## `.put(...values: List<Any>) -> Nil`

Add new values to the current set.

```lxm
set.put(value1, ..., valueN)
```

### Parameters

- **`values`**: all the values to add.

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Set`.

### Examples

```lxm
let set = set![1, 2, 3]

set.put(1, 5)
Debug.log(set)    -- set![1, 2, 3, 5]

set.put()
Debug.log(set)    -- set![1, 2, 3, 5]
```

## `.remove(...values: List<Any>) -> Nil`

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
Debug.log(set)    -- set![2, 3]

set.remove()
Debug.log(set)    -- set![2, 3]
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

Debug.log(set.toList())    -- [1, 2, 3]
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

Debug.log(set.toString())    -- "set![1, 2, 3]"
```

## `.clear() -> Nil`

Removes all elements from the set.

```lxm
set.clear()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Set`.

### Examples

```lxm
let set = set![1, 2, 3]

set.clear()

Debug.log(set)    -- set![]
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

Debug.log(left.add(right))        -- set![1, 2, 3, 4, 5, 6, 8]
Debug.log(left.add(nil))          -- BadArgumentError
Debug.log(left + right)           -- set![1, 2, 3, 4, 5, 6, 8] Implicit calling
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

Debug.log(left.sub(right))    -- set![1, 3, 5]
Debug.log(left.sub(nil))      -- BadArgumentError
Debug.log(left - right)       -- set![1, 3, 5] Implicit calling
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

Debug.log(left.logicAnd(right))   -- set![2, 4]
Debug.log(left.logicAnd(nil))     -- BadArgumentError
Debug.log(left & right)           -- set![2, 4] Implicit calling
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

Debug.log(left.logicOr(right))    -- set![1, 2, 3, 4, 5, 6, 8]
Debug.log(left.logicOr(nil))      -- BadArgumentError
Debug.log(left | right)           -- set![1, 2, 3, 4, 5, 6, 8] Implicit calling
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

Debug.log(left.logicXor(right))   -- set![1, 3, 5, 6, 8]
Debug.log(left.logicXor(nil))     -- BadArgumentError
Debug.log(left ^ right)           -- set![1, 3, 5, 6, 8] Implicit calling
```
