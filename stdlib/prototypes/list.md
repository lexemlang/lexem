
# Table of contents

- [Table of contents](#table-of-contents)
- [Methods](#methods)
  - [.size() -&gt; Integer](#size--gt-integer)
  - [.freeze() -&gt; Nil](#freeze--gt-nil)
  - [.isFrozen() -&gt; Logic](#isfrozen--gt-logic)
  - [.every(fn: Function) -&gt; Logic](#everyfn-function--gt-logic)
  - [.filter(fn: Function) -&gt; List](#filterfn-function--gt-list)
  - [.forEach(fn: Function) -&gt; Nil](#foreachfn-function--gt-nil)
  - [.find(fn: Function) -&gt; {index: Integer, value: Any} | Nil](#findfn-function--gt-index-integer-value-any--nil)
  - [.findLast(fn: Function) -&gt; {index: Integer, value: Any} | Nil](#findlastfn-function--gt-index-integer-value-any--nil)
  - [.indexOf(value: Any) -&gt; Integer | Nil](#indexofvalue-any--gt-integer--nil)
  - [.lastIndexOf(value: Any) -&gt; Integer | Nil](#lastindexofvalue-any--gt-integer--nil)
  - [.containsAny(...values: List&lt;Any&gt;) -&gt; Logic](#containsanyvalues-listltanygt--gt-logic)
  - [.containsAll(...values: List&lt;Any&gt;) -&gt; Logic](#containsallvalues-listltanygt--gt-logic)
  - [.map(fn: Function) -&gt; List](#mapfn-function--gt-list)
  - [.reduce(default: Any, fn: Function) -&gt; Any](#reducedefault-any-fn-function--gt-any)
  - [.any(fn: Function) -&gt; Logic](#anyfn-function--gt-logic)
  - [.remove(...values: List&lt;Any&gt;) -&gt; Nil](#removevalues-listltanygt--gt-nil)
  - [.removeAt(at: Integer) -&gt; Nil](#removeatat-integer--gt-nil)
  - [.removeAt(at: Integer, count: Integer) -&gt; Nil](#removeatat-integer-count-integer--gt-nil)
  - [.toString() -&gt; String](#tostring--gt-string)
  - [.joinToString() -&gt; String](#jointostring--gt-string)
  - [.joinToString(separator: String) -&gt; String](#jointostringseparator-string--gt-string)
  - [.copyWithin(target: List, at: Integer, from: Integer) -&gt; Nil](#copywithintarget-list-at-integer-from-integer--gt-nil)
  - [.copyWithin(target: List, at: Integer, from: Integer, count: Integer) -&gt; Nil](#copywithintarget-list-at-integer-from-integer-count-integer--gt-nil)
  - [.push(...values: List&lt;Any&gt;) -&gt; Nil](#pushvalues-listltanygt--gt-nil)
  - [.pop() -&gt; Any](#pop--gt-any)
  - [.pop(count: Integer) -&gt; List&lt;Any&gt;](#popcount-integer--gt-listltanygt)
  - [.unshift(...values: List&lt;Any&gt;) -&gt; Nil](#unshiftvalues-listltanygt--gt-nil)
  - [.shift() -&gt; Any](#shift--gt-any)
  - [.shift(count: Integer) -&gt; List&lt;Any&gt;](#shiftcount-integer--gt-listltanygt)
  - [.insert(at: Integer, ...values: List&lt;Any&gt;) -&gt; Nil](#insertat-integer-values-listltanygt--gt-nil)
  - [.replace(at: Integer, count: Integer, ...values: List&lt;Any&gt;) -&gt; Nil](#replaceat-integer-count-integer-values-listltanygt--gt-nil)
  - [.reverse() -&gt; Nil](#reverse--gt-nil)
  - [.slice(from: Integer) -&gt; List&lt;Any&gt;](#slicefrom-integer--gt-listltanygt)
  - [.slice(from: Integer, count: Integer) -&gt; List&lt;Any&gt;](#slicefrom-integer-count-integer--gt-listltanygt)
- [Accesses](#accesses)
  - [[index: Integer] -&gt; Any](#index-integer--gt-any)
  - [[index: Integer] = value: Any -&gt; Any](#index-integer--value-any--gt-any)

# Methods

## `.size() -> Integer`

Returns the number of elements in the current list.

```lxm
list.size()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `List`.

### Examples

```lxm
let list = [1, 2, 3]

Debug.log(list.size())    -- 3
```

## `.freeze() -> Nil`

Makes the list constant so it can't be extended, shrank or modified.

```lxm
list.freeze()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `List`.

### Examples

```lxm
let list = []

list.freeze()

Debug.log(list)       -- #[]
```

## `.isFrozen() -> Logic`

Whether the list is constant or not.

```lxm
list.isFrozen()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `List`.

### Examples

```lxm
let list = #[]

Debug.log(list.isFrozen())    -- true
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

Debug.log(list.every(gt0))    -- true
Debug.log(list.every(gt2))    -- false
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

Debug.log(list.filter(gt2))       -- [3]
Debug.log(list.filter(falseFn))   -- []
```

## `.forEach(fn: Function) -> Nil`

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

Debug.log(count)    -- 6
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

Debug.log(list.find(gt1))  -- {index: 1, value: 2}
Debug.log(list.find(gt5))  -- nil
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

Debug.log(list.findLast(gt1))  -- {index: 3, value: 5}
Debug.log(list.findLast(gt5))  -- nil
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

Debug.log(list.indexOf(2))  -- 1
Debug.log(list.indexOf(6))  -- nil
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

Debug.log(list.lastIndexOf(2))  -- 3
Debug.log(list.lastIndexOf(6))  -- nil
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

Debug.log(list.containsAny(1, 7, 9))   -- true
Debug.log(list.containsAny(-4, 5))     -- false
Debug.log(list.containsAny())          -- false
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

Debug.log(list.containsAll(1, 3))    -- true
Debug.log(list.containsAll(1, 5))    -- false
Debug.log(list.containsAll())        -- true
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

Debug.log(list.map(add10))   -- [11, 12, 13]
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

Debug.log(list.reduce(0, add))     -- 6
Debug.log(list.reduce(10, add))    -- 16
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

Debug.log(list.any(gt2)) -- true
Debug.log(list.any(gt5)) -- false
```

## `.remove(...values: List<Any>) -> Nil`

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
Debug.log(list)   -- [2, 3]

list.remove()
Debug.log(list)   -- [2, 3]
```

## `.removeAt(at: Integer) -> Nil`

Remove the element at the specified position.

```lxm
list.removeAt(at)
```

### Parameters

- **`at`**: the index to remove.

### Errors

- **`BadArgumentError`**: when the type of `at` is not a positive `Integer`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `List`.

### Examples

```lxm
let list = [1, 2, 3, 4, 5]

list.removeAt(1)

Debug.log(list)   -- [1, 3, 4, 5]
```

## `.removeAt(at: Integer, count: Integer) -> Nil`

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

Debug.log(list)   -- [1, 5]
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

Debug.log(list.toString())    -- "[1, 2, 3]"
```

## `.joinToString() -> String`

Return a `String` resulted from concatenating all the string representation of every cell in the list.

```lxm
list.joinToString()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `List`.

### Examples

```lxm
let list = [1, 2, 3]

Debug.log(list.joinToString())    -- "123"
```

## `.joinToString(separator: String) -> String`

Return a `String` resulted from concatenating all the string representation of every cell in the list separate by `separator`.

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

Debug.log(list.joinToString(",")) -- "1,2,3"
Debug.log(list.joinToString("--")) -- "1--2--3"
```

## `.copyWithin(target: List, at: Integer, from: Integer) -> Nil`

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

Debug.log(list)     -- [1, 2, 3, 4, 5]
Debug.log(target)   -- [10, 11, 2, 3, 4, 5]
```

## `.copyWithin(target: List, at: Integer, from: Integer, count: Integer) -> Nil`

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

Debug.log(list)     -- [1, 2, 3, 4, 5]
Debug.log(target)   -- [10, 11, 2, 3, 4]
```

## `.push(...values: List<Any>) -> Nil`

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
Debug.log(list)    -- [1, 2, 3, 1, 5]

list.push()
Debug.log(list)    -- [1, 2, 3, 1, 5]
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

Debug.log(list.pop())   -- 3
Debug.log(list)         -- [1, 2]
Debug.log(list.pop())   -- 2
Debug.log(list.pop())   -- 1
Debug.log(list)         -- []
Debug.log(list.pop())   -- Nil
```

## `.pop(count: Integer) -> List<Any>`

Removes the last `count` elements of the current list and returns them.

```lxm
list.pop(count)
```

### Parameters

- **`count`**: the number of elements to remove.

### Errors

- **`BadArgumentError`**: when the type of `count` is not a positive `Integer`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `List`.

### Examples

```lxm
let list = [1, 2, 3]

Debug.log(list.pop(2))  -- [3, 2]
Debug.log(list)         -- [1]
Debug.log(list.pop(2))  -- [1]
Debug.log(list)         -- []
Debug.log(list.pop(2))  -- []
```

## `.unshift(...values: List<Any>) -> Nil`

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
Debug.log(list)    -- [1, 5, 1, 2, 3]

list.unshift()
Debug.log(list)    -- [1, 5, 1, 2, 3]
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

Debug.log(list.shift())   -- 1
Debug.log(list)           -- [2, 3]
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

Debug.log(list.shift(2))  -- [1, 2]
Debug.log(list)           -- [3]
```

## `.insert(at: Integer, ...values: List<Any>) -> Nil`

Add new values at the specified position.

```lxm
list.insert(at, value1, ..., valueN)
```

### Parameters

- **`at`**: the index to insert the values.
- **`values`**: all the values to add.

### Errors

- **`BadArgumentError`**: when the type of `at` is not a positive `Integer`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `List`.

### Examples

```lxm
let list = [1, 2, 3]

list.insert(1, 5, 6, 7)
Debug.log(list)    -- [1, 5, 6, 7, 2, 3]

list.insert(4)
Debug.log(list)    -- [1, 5, 6, 7, 2, 3]
list.insert(20, 55)
Debug.log(list)    -- [1, 5, 6, 7, 2, 3, 55]
```

## `.replace(at: Integer, count: Integer, ...values: List<Any>) -> Nil`

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
Debug.log(list)    -- [1, 5, 6, 7, 3]
```

## `.reverse() -> Nil`

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

Debug.log(list)   -- [3, 2, 1]
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

Debug.log(list.slice(3))   -- [4, 5]
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

Debug.log(list.slice(1, 3))   -- [2, 3, 4]
```

# Accesses

## `[index: Integer] -> Any`

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

Debug.log(list[nil])  -- BadArgumentError
Debug.log(list[-3])   -- nil
Debug.log(list[-2])   -- 1
Debug.log(list[-1])   -- 2
Debug.log(list[0])    -- 1
Debug.log(list[1])    -- 2
Debug.log(list[2])    -- nil
```

## `[index: Integer] = value: Any -> Any`

Assigns `value` to the cell at `index` and returns `value`. When `index` is negative, it starts from the end of the list.

```lxm
list[index] = value
```

### Parameters

- **`index`**: the cell position starting with 0.

### Errors

- **`BadArgumentError`**: when the type of `index` is not an `Integer`.
- **`OutOfBoundsError`**: when the specified cell is out of bounds of the list.
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
