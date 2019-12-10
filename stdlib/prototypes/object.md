
# Table of contents

- [Table of contents](#table-of-contents)
- [Methods](#methods)
  - [.freeze() -&gt; Nil](#freeze--gt-nil)
  - [.isFrozen() -&gt; Logic](#isfrozen--gt-logic)
  - [.freezeProperties(...properties: List&lt;String&gt;) -&gt; Nil](#freezepropertiesproperties-listltstringgt--gt-nil)
  - [.freezeAllProperties() -&gt; Nil](#freezeallproperties--gt-nil)
  - [.removeProperties(...properties: List&lt;String&gt;) -&gt; Nil](#removepropertiesproperties-listltstringgt--gt-nil)
  - [.getOwnPropertyKeys() -&gt; List&lt;String&gt;](#getownpropertykeys--gt-listltstringgt)
  - [.getOwnPropertyValues() -&gt; List&lt;Any&gt;](#getownpropertyvalues--gt-listltanygt)
  - [.getOwnProperties() -&gt; List&lt;{key:String, value:Any}&gt;](#getownproperties--gt-listltkeystring-valueanygt)
  - [.ownPropertiesToMap() -&gt; Map&lt;String, Any&gt;](#ownpropertiestomap--gt-mapltstring-anygt)
  - [.containsAnyOwnProperties(...properties: List&lt;String&gt;) -&gt; Logic](#containsanyownpropertiesproperties-listltstringgt--gt-logic)
  - [.containsAllOwnProperties(...properties: List&lt;String&gt;) -&gt; Logic](#containsallownpropertiesproperties-listltstringgt--gt-logic)
- [Accesses](#accesses)
  - [[property: String] -&gt; Any](#property-string--gt-any)
  - [[property: String] = value: Any -&gt; Any](#property-string--value-any--gt-any)

# Methods

## `.freeze() -> Nil`

Makes the object constant so it can't be extended, shrank or modified.

```lxm
object.freeze()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not an `Object`.

### Examples

```lxm
let object = {}

object.freeze()

Debug.log(object)     -- #{}
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

Debug.log(object.isFrozen())  -- true
```

## `.freezeProperties(...properties: List<String>) -> Nil`

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

Debug.log(object)     -- {#a: 1, #b: 2, c: 3}
```

## `.freezeAllProperties() -> Nil`

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

Debug.log(object)     -- {#a: 1, #b: 2, #c: 3}
```

## `.removeProperties(...properties: List<String>) -> Nil`

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

Debug.log(object)     -- {c: 3}
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

Debug.log(object.getOwnPropertyKeys())    -- ["a", "b", "c"]
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

Debug.log(object.getOwnPropertyValues())    -- [1, 2, 3]
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

Debug.log(object.getOwnProperties())    -- [{key: "a", value: 1}, {key: "b", value: 2}]
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

Debug.log(object.ownPropertiesToMap())    -- @{a: 1, b: 2, c: 3}
```

## `.containsAnyOwnProperties(...properties: List<String>) -> Logic`

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

Debug.log(object.containsAnyOwnProperties("a", "l"))     -- true
Debug.log(object.containsAnyOwnProperties("f", "g"))     -- false
```

## `.containsAllOwnProperties(...properties: List<String>) -> Logic`

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

Debug.log(object.containsAllOwnProperties("a", "b"))     -- true
Debug.log(object.containsAllOwnProperties("b", "g"))     -- false
```

# Accesses

## `[property: String] -> Any`

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

Debug.log(object[nil])  -- BadArgumentError
Debug.log(object["a"])  -- 1
Debug.log(object["b"])  -- 2
Debug.log(object["c"])  -- nil
```

## `[property: String] = value: Any -> Any`

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
