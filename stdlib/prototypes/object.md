
# Table of contents

- [Table of contents](#table-of-contents)
- [Methods](#methods)
  - [`.freeze()`](#freeze)
    - [Errors](#errors)
    - [Examples](#examples)
  - [`.isFrozen() -> Logic`](#isfrozen---logic)
    - [Errors](#errors-1)
    - [Examples](#examples-1)
  - [`.not() -> Logic`](#not---logic)
    - [Examples](#examples-2)
  - [`.freezeProperties(...properties: List<String>)`](#freezepropertiesproperties-liststring)
    - [Parameters](#parameters)
    - [Errors](#errors-2)
    - [Examples](#examples-3)
  - [`.freezeAllProperties()`](#freezeallproperties)
    - [Errors](#errors-3)
    - [Examples](#examples-4)
  - [`.removeProperties(...properties: List<String>)`](#removepropertiesproperties-liststring)
    - [Parameters](#parameters-1)
    - [Errors](#errors-4)
    - [Examples](#examples-5)
  - [`.getOwnPropertyKeys() -> List<String>`](#getownpropertykeys---liststring)
    - [Errors](#errors-5)
    - [Examples](#examples-6)
  - [`.getOwnPropertyValues() -> List<Any>`](#getownpropertyvalues---listany)
    - [Errors](#errors-6)
    - [Examples](#examples-7)
  - [`.getOwnProperties() -> List<{key:String, value:Any}>`](#getownproperties---listkeystring-valueany)
    - [Errors](#errors-7)
    - [Examples](#examples-8)
  - [`.ownPropertiesToMap() -> Map<String, Any>`](#ownpropertiestomap---mapstring-any)
    - [Errors](#errors-8)
    - [Examples](#examples-9)
  - [`.containsAnyOwnProperties(...properties: List<String>)`](#containsanyownpropertiesproperties-liststring)
    - [Parameters](#parameters-2)
    - [Errors](#errors-9)
    - [Examples](#examples-10)
  - [`.containsAllOwnProperties(...properties: List<String>)`](#containsallownpropertiesproperties-liststring)
    - [Parameters](#parameters-3)
    - [Errors](#errors-10)
    - [Examples](#examples-11)
- [Accesses](#accesses)
  - [`.index(property: String) -> Any`](#indexproperty-string---any)
    - [Parameters](#parameters-4)
    - [Errors](#errors-11)
    - [Examples](#examples-12)
  - [`.index(property: String, value: Any) -> Any`](#indexproperty-string-value-any---any)
    - [Parameters](#parameters-5)
    - [Errors](#errors-12)
    - [Examples](#examples-13)

# Methods

## `.freeze()`

Makes the object constant so it can't be extended, shrinked or modified.

```lxm
object.freeze()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not an `Object`.

### Examples

```lxm
let object = {}

object.freeze()

log(object)     -- #{}
```

## `.isFrozen() -> Logic`

Whether the object is constant or not.

```lxm
object.isFrozen()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not an `Object`.

### Examples

```lxm
let object = #{}

log(object.isFrozen())  -- true
```

## `.not() -> Logic`

Returns `true` if the object is falsey (i.e. `nil`), otherwise returns `false`.

```lxm
object.not()
```

### Examples

```lxm
let object = #{}

if(object) {}   -- Equivalent to: if(object.not() === false) {}  
```

## `.freezeProperties(...properties: List<String>)`

Makes every specified property constant. If any of the specified properties do not exist, they are ignored.

```lxm
object.freezeProperties(propName1, ..., propNameN)
```

### Parameters

- **`properties`**: the property names to make constant.

### Errors

- **`BadArgumentError`**: when the type of any property is not a `String`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not an `Object`.

### Examples

```lxm
let object = {a: 1, b: 2, c: 3}

object.freezeProperties("a", "b")

log(object)     -- {#a: 1, #b: 2, c: 3}
```

## `.freezeAllProperties()`

Makes all the properties of the object constant.

```lxm
object.freezeAllProperties()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not an `Object`.

### Examples

```lxm
let object = {a: 1, b: 2, c: 3}

object.freezeAllProperties()

log(object)     -- {#a: 1, #b: 2, #c: 3}
```

## `.removeProperties(...properties: List<String>)`

Removes all specified properties from the object. If any of the specified properties do not exist, they are ignored.

```lxm
object.freezeProperty(propName1, ..., propNameN)
```

### Parameters

- **`properties`**: the property names to make constant.

### Errors

- **`BadArgumentError`**: when the type of any property is not a `String`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not an `Object`.

### Examples

```lxm
let object = {a: 1, b: 2, c: 3}

object.removeProperties("a", "b")

log(object)     -- {c: 3}
```

## `.getOwnPropertyKeys() -> List<String>`

Returns a list with all the property names of the object.

```lxm
object.getOwnPropertyKeys()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not an `Object`.

### Examples

```lxm
let object = {a: 1, b: 2, c: 3}

log(object.getOwnPropertyKeys())    -- ["a", "b", "c"]
```

## `.getOwnPropertyValues() -> List<Any>`

Returns a list with all the values of each property of the object.

```lxm
object.getOwnPropertyValues()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not an `Object`.

### Examples

```lxm
let object = {a: 1, b: 2, c: 3}

log(object.getOwnPropertyValues())    -- [1, 2, 3]
```

## `.getOwnProperties() -> List<{key:String, value:Any}>`

Returns a list with all the properties of the object.

```lxm
object.getOwnProperties()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not an `Object`.

### Examples

```lxm
let object = {a: 1, b: 2}

log(object.getOwnProperties())    -- [{key: "a", value: 1}, {key: "b", value: 2}]
```

## `.ownPropertiesToMap() -> Map<String, Any>`

Returns a map with all the properties of the object.

```lxm
object.ownPropertiesToMap()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not an `Object`.

### Examples

```lxm
let object = {a: 1, b: 2, c: 3}

log(object.ownPropertiesToMap())    -- @{a: 1, b: 2, c: 3}
```

## `.containsAnyOwnProperties(...properties: List<String>)`

Returns whether the object contains any of the specified properties.

```lxm
object.containsAnyOwnProperties(propName1, ..., propNameN)
```

### Parameters

- **`properties`**: the property names to make constant.

### Errors

- **`BadArgumentError`**: when the type of any property is not a `String`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not an `Object`.

### Examples

```lxm
let object = {a: 1, b: 2, c: 3}

log(object.containsAnyOwnProperties("a", "l"))     -- true
log(object.containsAnyOwnProperties("f", "g"))     -- false
```

## `.containsAllOwnProperties(...properties: List<String>)`

Returns whether the object contains all the specified properties.

```lxm
object.containsAllOwnProperties(propName1, ..., propNameN)
```

### Parameters

- **`properties`**: the property names to make constant.

### Errors

- **`BadArgumentError`**: when the type of any property is not a `String`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not an `Object`.

### Examples

```lxm
let object = {a: 1, b: 2, c: 3}

log(object.containsAllOwnProperties("a", "b"))     -- true
log(object.containsAllOwnProperties("b", "g"))     -- false
```

# Accesses

## `.index(property: String) -> Any`

Returns the value of the property called `property` or `nil` if the property does not exist. 

```lxm
object[index]
```

### Parameters

- **`property`**: the property name.

### Errors

- **`BadArgumentError`**: when the type of `property` is not a `String`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Object`.

### Examples

```lxm
let object = {a: 1, b: 2}

log(object[nil])  -- BadArgumentError
log(object["a"])  -- 1
log(object["b"])  -- 2
log(object["c"])  -- nil
```

## `.index(property: String, value: Any) -> Any`

Assigns `value` to the property called `property` and returns `value`. When `property` does not exist, it is added.

```lxm
object[index] = value
```

### Parameters

- **`property`**: the property name.

### Errors

- **`BadArgumentError`**: when the type of `property` is not a `String`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Object`.

### Examples

```lxm
let object = {a: 1}

object[nil] = 1   -- BadArgumentError
object["a"] = 3   -- object = {a: 3}
object["b"] = 4   -- object = {a: 3, b: 4}
```
