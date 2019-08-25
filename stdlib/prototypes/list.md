
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
  - [`.filter(fn: Function) -> List`](#filterfn-function---list)
    - [Parameters](#parameters-1)
    - [Errors](#errors-2)
    - [Examples](#examples-2)
  - [`.forEach(fn: Function)`](#foreachfn-function)
    - [Parameters](#parameters-2)
    - [Errors](#errors-3)
    - [Examples](#examples-3)
  - [`.find(fn: Function) -> {index: Integer, value: Any} | Nil`](#findfn-function---index-integer-value-any--nil)
    - [Parameters](#parameters-3)
    - [Errors](#errors-4)
    - [Examples](#examples-4)
  - [`.findLast(fn: Function) -> {index: Integer, value: Any} | Nil`](#findlastfn-function---index-integer-value-any--nil)
    - [Parameters](#parameters-4)
    - [Errors](#errors-5)
    - [Examples](#examples-5)
  - [`.indexOf(value: Any) -> Integer | Nil`](#indexofvalue-any---integer--nil)
    - [Parameters](#parameters-5)
    - [Errors](#errors-6)
    - [Examples](#examples-6)
  - [`.lastIndexOf(value: Any) -> Integer | Nil`](#lastindexofvalue-any---integer--nil)
    - [Parameters](#parameters-6)
    - [Errors](#errors-7)
    - [Examples](#examples-7)
  - [`.containsAny(...values: List<Any>) -> Logic`](#containsanyvalues-listany---logic)
    - [Parameters](#parameters-7)
    - [Errors](#errors-8)
    - [Examples](#examples-8)
  - [`.containsAll(...values: List<Any>) -> Logic`](#containsallvalues-listany---logic)
    - [Parameters](#parameters-8)
    - [Errors](#errors-9)
    - [Examples](#examples-9)
  - [`.map(fn: Function) -> List`](#mapfn-function---list)
    - [Parameters](#parameters-9)
    - [Errors](#errors-10)
    - [Examples](#examples-10)
  - [`.reduce(default: Any, fn: Function) -> Any`](#reducedefault-any-fn-function---any)
    - [Parameters](#parameters-10)
    - [Errors](#errors-11)
    - [Examples](#examples-11)
  - [`.any(fn: Function) -> Logic`](#anyfn-function---logic)
    - [Parameters](#parameters-11)
    - [Errors](#errors-12)
    - [Examples](#examples-12)
  - [`.remove(...values: List<Any>)`](#removevalues-listany)
    - [Parameters](#parameters-12)
    - [Errors](#errors-13)
    - [Examples](#examples-13)
  - [`.removeAt(at: Integer)`](#removeatat-integer)
    - [Parameters](#parameters-13)
    - [Errors](#errors-14)
    - [Examples](#examples-14)
  - [`.removeAt(at: Integer, count: Integer)`](#removeatat-integer-count-integer)
    - [Parameters](#parameters-14)
    - [Errors](#errors-15)
    - [Examples](#examples-15)
  - [`.toList() -> List`](#tolist---list)
    - [Errors](#errors-16)
    - [Examples](#examples-16)
  - [`.toString() -> String`](#tostring---string)
    - [Errors](#errors-17)
    - [Examples](#examples-17)
  - [`.joinToString() -> String`](#jointostring---string)
    - [Errors](#errors-18)
    - [Examples](#examples-18)
  - [`.joinToString(separator: String) -> String`](#jointostringseparator-string---string)
    - [Parameters](#parameters-15)
    - [Errors](#errors-19)
    - [Examples](#examples-19)
  - [`.copyWithin(target: List, at: Integer, from: Integer)`](#copywithintarget-list-at-integer-from-integer)
    - [Parameters](#parameters-16)
    - [Errors](#errors-20)
    - [Examples](#examples-20)
  - [`.copyWithin(target: List, at: Integer, from: Integer, count: Integer)`](#copywithintarget-list-at-integer-from-integer-count-integer)
    - [Parameters](#parameters-17)
    - [Errors](#errors-21)
    - [Examples](#examples-21)
  - [`.push(...values: List<Any>)`](#pushvalues-listany)
    - [Parameters](#parameters-18)
    - [Errors](#errors-22)
    - [Examples](#examples-22)
  - [`.pop() -> Any`](#pop---any)
    - [Errors](#errors-23)
    - [Examples](#examples-23)
  - [`.pop(count: Integer) -> List<Any>`](#popcount-integer---listany)
    - [Parameters](#parameters-19)
    - [Errors](#errors-24)
    - [Examples](#examples-24)
  - [`.unshift(...values: List<Any>)`](#unshiftvalues-listany)
    - [Parameters](#parameters-20)
    - [Errors](#errors-25)
    - [Examples](#examples-25)
  - [`.shift() -> Any`](#shift---any)
    - [Errors](#errors-26)
    - [Examples](#examples-26)
  - [`.shift(count: Integer) -> List<Any>`](#shiftcount-integer---listany)
    - [Parameters](#parameters-21)
    - [Errors](#errors-27)
    - [Examples](#examples-27)
  - [`.insert(at: Integer, ...values: List<Any>)`](#insertat-integer-values-listany)
    - [Parameters](#parameters-22)
    - [Errors](#errors-28)
    - [Examples](#examples-28)
  - [`.replace(at: Integer, count: Integer, ...values: List<Any>)`](#replaceat-integer-count-integer-values-listany)
    - [Parameters](#parameters-23)
    - [Errors](#errors-29)
    - [Examples](#examples-29)
  - [`.reverse()`](#reverse)
    - [Errors](#errors-30)
    - [Examples](#examples-30)
  - [`.slice(from: Integer) -> List<Any>`](#slicefrom-integer---listany)
    - [Parameters](#parameters-24)
    - [Errors](#errors-31)
    - [Examples](#examples-31)
  - [`.slice(from: Integer, count: Integer) -> List<Any>`](#slicefrom-integer-count-integer---listany)
    - [Parameters](#parameters-25)
    - [Errors](#errors-32)
    - [Examples](#examples-32)
  - [`.sort()`](#sort)
    - [Errors](#errors-33)
    - [Examples](#examples-33)
- [Accesses](#accesses)
  - [`.index(index: Integer) -> Any`](#indexindex-integer---any)
    - [Parameters](#parameters-26)
    - [Errors](#errors-34)
    - [Examples](#examples-34)
  - [`.index(index: Integer, value: Any) -> Any`](#indexindex-integer-value-any---any)
    - [Parameters](#parameters-27)
    - [Errors](#errors-35)
    - [Examples](#examples-35)

# Methods

## `.size()`

Returns the number of elements in the current list.

```lxm
list.size()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `List`.

### Examples

```lxm
let list = [1, 2, 3]

log(list.size())    -- 3
```

## `.every(fn: Function) -> Logic`

Returns `true` if `fn` returns a truthy value for every element in the list, otherwise returns `false`.

```lxm
list.every(fn)
```

### Parameters

- **`fn`**: the function to execute once per value in the list.

### Errors

- **`BadArgumentError`**: when the type of `fn` is not a `Function`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `List`.

### Examples

```lxm
let list = [1, 2, 3]

fun gt0(value, index) { return value > 0 }
fun gt2(value, index) { return value > 2 }

log(list.every(gt0))    -- true
log(list.every(gt2))    -- false
```

## `.filter(fn: Function) -> List`

Returns a new list with only the values for which `fn` returns a truthy value.

```lxm
list.filter(fn)
```

### Parameters

- **`fn`**: the function to execute once per value in the list.

### Errors

- **`BadArgumentError`**: when the type of `fn` is not a `Function`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `List`.

### Examples

```lxm
let list = [1, 2, 3]

fun gt2(value, index) { return value > 2 }
fun falseFn(value, index) { return false }

log(list.filter(gt2))       -- [3]
log(list.filter(falseFn))   -- []
```

## `.forEach(fn: Function)`

Executes a function once per element in the current list.

```lxm
list.forEach(fn)
```

### Parameters

- **`fn`**: the function to execute once per value in the list.

### Errors

- **`BadArgumentError`**: when the type of `fn` is not a `Function`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `List`.

### Examples

```lxm
let list = [1, 2, 3]

var count = 0
fun add(value, index) { count + value }

list.forEach(add)

log(count)    -- 6
```

## `.find(fn: Function) -> {index: Integer, value: Any} | Nil`

Returns the index and value of the first element for which `fn` returns a truthy value or `nil` otherwise.

```lxm
list.find(fn)
```

### Parameters

- **`fn`**: the function to execute once per value in the list.

### Errors

- **`BadArgumentError`**: when the type of `fn` is not a `Function`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `List`.

### Examples

```lxm
let list = [1, 2, 3]

fun gt1(value, index) { return value > 1 }
fun gt5(value, index) { return value > 5 }

log(list.find(gt1))  -- {index: 1, value: 2}
log(list.find(gt5))  -- nil
```

## `.findLast(fn: Function) -> {index: Integer, value: Any} | Nil`

Returns the index and value of the last element for which `fn` returns a truthy value or `nil` otherwise.

```lxm
list.findLast(fn)
```

### Parameters

- **`fn`**: the function to execute once per value in the list.

### Errors

- **`BadArgumentError`**: when the type of `fn` is not a `Function`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `List`.

### Examples

```lxm
let list = [1, 2, 3, 5]

fun gt1(value, index) { return value > 1 }
fun gt5(value, index) { return value > 5 }

log(list.findLast(gt1))  -- {index: 3, value: 5}
log(list.findLast(gt5))  -- nil
```

## `.indexOf(value: Any) -> Integer | Nil`

Returns the index of the first cell that contains the `value` or `nil` if it is not contained inside the current list.

```lxm
list.indexOf(value)
```

### Parameters

- **`value`**: the value to search.

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `List`.

### Examples

```lxm
let list = [1, 2, 3, 2]

log(list.indexOf(2))  -- 1
log(list.indexOf(6))  -- nil
```

## `.lastIndexOf(value: Any) -> Integer | Nil`

Returns the index of the last cell that contains the `value` or `nil` if it is not contained inside the current list.

```lxm
list.lastIndexOf(value)
```

### Parameters

- **`value`**: the value to search.

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `List`.

### Examples

```lxm
let list = [1, 2, 3, 2]

log(list.lastIndexOf(2))  -- 3
log(list.lastIndexOf(6))  -- nil
```

## `.containsAny(...values: List<Any>) -> Logic`

Returns a `Logic` value indicating whether any of the values are present in the current list. The function returns `false` if there is no values.

```lxm
list.containsAny(value1, ..., valueN)
```

### Parameters

- **`values`**: all the values to check.

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `List`.

### Examples

```lxm
let list = [1, 2, 3]

log(list.containsAny(1, 7, 9))   -- true
log(list.containsAny(-4, 5))     -- false
log(list.containsAny())          -- false
```

## `.containsAll(...values: List<Any>) -> Logic`

Returns a `Logic` value indicating whether all the the values are present in the current list. The function returns `true` if there is no values.

```lxm
list.containsAll(value1, ..., valueN)
```

### Parameters

- **`values`**: all the values to check.

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `List`.

### Examples

```lxm
let list = [1, 2, 3]

log(list.containsAll(1, 3))    -- true
log(list.containsAll(1, 5))    -- false
log(list.containsAll())        -- true
```

## `.map(fn: Function) -> List`

Returns a new `List` filled with the values returned by `fn` fo each value.

```lxm
list.map(fn)
```

### Parameters

- **`fn`**: the function to execute once per value in the list.

### Errors

- **`BadArgumentError`**: when the type of `fn` is not a `Function`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `List`.

### Examples

```lxm
let list = [1, 2, 3]

fun add10(value, index) { return value + 10 }

log(list.map(add10))   -- [11, 12, 13]
```

## `.reduce(default: Any, fn: Function) -> Any`

Returns the accumulated value of processing with `fn` all values of the current list.

```lxm
list.reduce(default, fn)
```

### Parameters

- **`default`**: the default value to accumulate the result.
- **`fn`**: the function to execute once per value in the list.

### Errors

- **`BadArgumentError`**: when the type of `fn` is not a `Function`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `List`.

### Examples

```lxm
let list = [1, 2, 3]

fun add(accumulation, value, index) { return accumulation + value }

log(list.reduce(0, add))     -- 6
log(list.reduce(10, add))    -- 16
```

## `.any(fn: Function) -> Logic`

Returns `true` if `fn` returns a truthy value for any of the elements in the list, otherwise returns `false`.

```lxm
list.any(fn)
```

### Parameters

- **`fn`**: the function to execute once per value in the list.

### Errors

- **`BadArgumentError`**: when the type of `fn` is not a `Function`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `List`.

### Examples

```lxm
let list = [1, 2, 3]

fun gt2(value, index) { return value > 2 }
fun gt5(value, index) { return value > 5 }

log(list.any(gt2)) -- true
log(list.any(gt5)) -- false
```

## `.remove(...values: List<Any>)`

Remove some values from the current list. If any value is repeated, all the copies are removed.

```lxm
list.remove(value1, ..., valueN)
```

### Parameters

- **`values`**: all the values to remove.

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `List`.

### Examples

```lxm
let list = [1, 2, 3, 1]

list.remove(1, 5)
log(list)   -- [2, 3]

list.remove()
log(list)   -- [2, 3]
```

## `.removeAt(at: Integer)`

Remove the element at the specified position.

```lxm
list.removeAt(at)
```

### Parameters

- **`at`**: the index to remove.

### Errors

- **`BadArgumentError`**: when the type of `at` is not an `Integer`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `List`.

### Examples

```lxm
let list = [1, 2, 3, 4, 5]

list.removeAt(1)

log(list)   -- [1, 3, 4, 5]
```

## `.removeAt(at: Integer, count: Integer)`

Remove `count` elements from the current list starting from `at`.

```lxm
list.removeAt(at, count)
```

### Parameters

- **`at`**: the starting index.
- **`count`**: the number of elements to remove.

### Errors

- **`BadArgumentError`**: when the type of any argument is incorrect.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `List`.

### Examples

```lxm
let list = [1, 2, 3, 4, 5]

list.removeAt(1, 3)

log(list)   -- [1, 5]
```

## `.toList() -> List`

Transforms the current list into a `List`. The order is not guaranteed.

```lxm
list.toList()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `List`.

### Examples

```lxm
let list = [1, 2, 3]

log(list.toList())    -- [1, 2, 3]
```

## `.toString() -> String`

Return the `String` representation of the current list.

```lxm
list.toString()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `List`.

### Examples

```lxm
let list = [1, 2, 3]

log(list.toString())    -- "[1, 2, 3]"
```

## `.joinToString() -> String`

Return a `String` resulted from concating all the string representation of every cell in the list.

```lxm
list.joinToString()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `List`.

### Examples

```lxm
let list = [1, 2, 3]

log(list.joinToString())    -- "123"
```

## `.joinToString(separator: String) -> String`

Return a `String` resulted from concating all the string representation of every cell in the list separate by `separator`.

```lxm
list.joinToString(fn)
```

### Parameters

- **`separator`**: the string that separate the each string representation.

### Errors

- **`BadArgumentError`**: when the type of `separator` is not a `String`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `List`.

### Examples

```lxm
let list = [1, 2, 3]

log(list.joinToString(",")) -- "1,2,3"
log(list.joinToString("--")) -- "1--2--3"
```

## `.copyWithin(target: List, at: Integer, from: Integer)`

Copy all the elements of the current list from `from` into `target` starting at `at`.

```lxm
list.copyWithin(target, at, from, count)
```

### Parameters

- **`other`**: the target list.
- **`at`**: the starting index in the target list.
- **`from`**: the starting index in the current list.

### Errors

- **`BadArgumentError`**: when the type of any argument is incorrect.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `List`.

### Examples

```lxm
let list = [1, 2, 3, 4, 5]
let target = [10, 11, 12]

list.copyWithin(target, 2, 1)

log(list)     -- [1, 2, 3, 4, 5]
log(target)   -- [10, 11, 2, 3, 4, 5]
```

## `.copyWithin(target: List, at: Integer, from: Integer, count: Integer)`

Copy `count` elements from `from` of the current list into `target` starting at `at`.

```lxm
list.copyWithin(target, at, from, count)
```

### Parameters

- **`other`**: the target list.
- **`at`**: the starting index in the target list.
- **`from`**: the starting index in the current list.
- **`count`**: the number of elements to copy.

### Errors

- **`BadArgumentError`**: when the type of any argument is incorrect.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `List`.

### Examples

```lxm
let list = [1, 2, 3, 4, 5]
let target = [10, 11, 12]

list.copyWithin(target, 2, 1, 3)

log(list)     -- [1, 2, 3, 4, 5]
log(target)   -- [10, 11, 2, 3, 4]
```

## `.push(...values: List<Any>)`

Add new values at the end of the current list.

```lxm
list.push(value1, ..., valueN)
```

### Parameters

- **`values`**: all the values to add.

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `List`.

### Examples

```lxm
let list = [1, 2, 3]

list.push(1, 5)
log(list)    -- [1, 2, 3, 1, 5]

list.push()
log(list)    -- [1, 2, 3, 1, 5]
```

## `.pop() -> Any`

Removes the last element of the current list and returns it.

```lxm
list.pop()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `List`.

### Examples

```lxm
let list = [1, 2, 3]

log(list.pop())   -- 3
log(list)         -- [1, 2]
```

## `.pop(count: Integer) -> List<Any>`

Removes the last `count` elements of the current list and returns them.

```lxm
list.pop(count)
```

### Parameters

- **`count`**: the number of elements to remove.

### Errors

- **`BadArgumentError`**: when the type of `count` is not an `Integer`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `List`.

### Examples

```lxm
let list = [1, 2, 3]

log(list.pop(2))  -- [3, 2]
log(list)         -- [1]
```

## `.unshift(...values: List<Any>)`

Add new values at the beginning of the current list.

```lxm
list.unshift(value1, ..., valueN)
```

### Parameters

- **`values`**: all the values to add.

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `List`.

### Examples

```lxm
let list = [1, 2, 3]

list.unshift(1, 5)
log(list)    -- [1, 5, 1, 2, 3]

list.unshift()
log(list)    -- [1, 5, 1, 2, 3]
```

## `.shift() -> Any`

Removes the first element of the current list and returns it.

```lxm
list.shift()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `List`.

### Examples

```lxm
let list = [1, 2, 3]

log(list.shift())   -- 1
log(list)           -- [2, 3]
```

## `.shift(count: Integer) -> List<Any>`

Removes the first `count` elements of the current list and returns them.

```lxm
list.shift(count)
```

### Parameters

- **`count`**: the number of elements to remove.

### Errors

- **`BadArgumentError`**: when the type of `count` is not an `Integer`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `List`.

### Examples

```lxm
let list = [1, 2, 3]

log(list.shift(2))  -- [1, 2]
log(list)           -- [3]
```

## `.insert(at: Integer, ...values: List<Any>)`

Add new values at the specified position.

```lxm
list.insert(at, value1, ..., valueN)
```

### Parameters

- **`at`**: the index to insert the values.
- **`values`**: all the values to add.

### Errors

- **`BadArgumentError`**: when the type of `at` is not an `Integer`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `List`.

### Examples

```lxm
let list = [1, 2, 3]

list.insert(1, 5, 6, 7)
log(list)    -- [1, 5, 6, 7, 2, 3]

list.insert(4)
log(list)    -- [1, 5, 6, 7, 2, 3]
```

## `.replace(at: Integer, count: Integer, ...values: List<Any>)`

Replace `count` elements of the current list at `at` for the specified values.

```lxm
list.replace(at, count, value1, ..., valueN)
```

### Parameters

- **`at`**: the index to insert the values.
- **`count`**: the number of elements to replace.
- **`values`**: all the values to add.

### Errors

- **`BadArgumentError`**: when the type of any argument is incorrect.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `List`.

### Examples

```lxm
let list = [1, 2, 3]

list.replace(1, 1, 5, 6, 7)
log(list)    -- [1, 5, 6, 7, 3]
```

## `.reverse()`

Reverse the current list.

```lxm
list.reverse()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `List`.

### Examples

```lxm
let list = [1, 2, 3]

list.reverse()

log(list)   -- [3, 2, 1]
```

## `.slice(from: Integer) -> List<Any>`

Returns a new list with all the elements after `from` (included) of the current list.

```lxm
list.slice(from)
```

### Parameters

- **`from`**: the starting index.

### Errors

- **`BadArgumentError`**: when the type of `from` is not an `Integer`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `List`.

### Examples

```lxm
let list = [1, 2, 3, 4, 5]

log(list.slice(3))   -- [4, 5]
```

## `.slice(from: Integer, count: Integer) -> List<Any>`

Returns a new list with `count` elements from `from` of the current list.

```lxm
list.slice(from, count)
```

### Parameters

- **`from`**: the starting index.
- **`count`**: the number of elements to get.

### Errors

- **`BadArgumentError`**: when the type of any argument is incorrect.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `List`.

### Examples

```lxm
let list = [1, 2, 3, 4, 5]

log(list.slice(1, 3))   -- [2, 3, 4]
```

## `.sort()`

Sorts the current list.

```lxm
list.sort()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `List`.

### Examples

```lxm
let list = [3, false, 1, "b", 2, [], {}, true,  "A"]

list.sort()

log(list)   -- [true, false, 1, 2, 3, "A", "b", [], {}]
```

# Accesses

## `.index(index: Integer) -> Any`

Returns the value in the cell at `index` or `nil` if the cell does not exist. When `index` is negative, it starts from the end of the list.

```lxm
list[index]
```

### Parameters

- **`index`**: the cell position starting with 0.

### Errors

- **`BadArgumentError`**: when the type of `index` is not an `Integer`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `List`.

### Examples

```lxm
let list = [1, 2]

log(list[nil])  -- BadArgumentError
log(list[-3])   -- nil
log(list[-2])   -- 1
log(list[-1])   -- 2
log(list[0])    -- 1
log(list[1])    -- 2
log(list[2])    -- nil
```

## `.index(index: Integer, value: Any) -> Any`

Assigns `value` to the cell at `index` and returns `value`. When `index` is negative, it starts from the end of the list.

```lxm
list[index] = value
```

### Parameters

- **`index`**: the cell position starting with 0.

### Errors

- **`BadArgumentError`**: when the type of `index` is not an `Integer`.
- **`OutOfBoundsError`**: when the specifid cell is out of bounds of the list.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `List`.

### Examples

```lxm
let list = [true]

list[nil] = 1   -- BadArgumentError
list[-2] = 2    -- OutOfBoundsError
list[-1] = 3    -- list = [3]
list[0] = 4     -- list = [3]
list[1] = 5     -- OutOfBoundsError
```
