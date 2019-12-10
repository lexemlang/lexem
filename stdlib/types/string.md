
# Table of contents

- [Table of contents](#table-of-contents)
- [Methods](#methods)
  - [.join(...values: List&lt;Any&gt;) -&gt; String](#joinvalues-listltanygt--gt-string)
  - [.joinBy(separator:String, ...values: List&lt;Any&gt;) -&gt; String](#joinbyseparatorstring-values-listltanygt--gt-string)
  - [.fromUnicodePoints(...charCodes: List&lt;Integer&gt;) -&gt; String](#fromunicodepointscharcodes-listltintegergt--gt-string)
- [Properties](#properties)
  - [.prototype -&gt; Object](#prototype--gt-object)

# Methods

## `.join(...values: List<Any>) -> String`

Returns a `String` that results from join every string representation of the specified objects.

```lxm
String.join(value1, ..., valueN)
```

### Parameters

- **`values`**: the values to join.

### Examples

```lxm
Debug.log(String.join(1, nil, true))     -- "1niltrue"
Debug.log(String.join())                 -- ""
```

## `.joinBy(separator:String, ...values: List<Any>) -> String`

Returns a `String` that results from join every string representation of the specified objects separating them by `separator`.

```lxm
String.joinBy(separator = value, value1, ..., valueN)
```

> **WARN**: it must be called with `separator` as named argument to not confuse with the other overloading of the function.

### Parameters

- **`separator`**: the string that acts as the separator of the values.
- **`values`**: the values to join.

### Errors

- **`BadArgumentError`**: when the type of `separator` is not a `String`.

### Examples

```lxm
Debug.log(String.joinBy(separator = ",", 1, nil, true))   -- "1,nil,true"
Debug.log(String.joinBy(separator = ","))                 -- ""
Debug.log(String.joinBy(separator = nil))                 -- BadArgumentError
```

## `.fromUnicodePoints(...charCodes: List<Integer>) -> String`

Returns a `String` compose for all the characters got from the their codes.

```lxm
String.fromUnicodePoints(charCode1, ..., charCodeN)
```

### Parameters

- **`charCodes`**: the code of every character in the resulting string.

### Errors

- **`BadArgumentError`**: when the type of any character code is not an `Integer` in the range `[0, 0x10FFFF]`.

### Examples

```lxm
Debug.log(String.fromUnicodePoints(0x74, 0x68, 0x69, 0x73, 0x61))    -- "thisa"
Debug.log(String.fromUnicodePoints(nil))                             -- BadArgumentError
```

# Properties

## `.prototype -> Object`

The prototype of the type.

```lxm
String.prototype
```
