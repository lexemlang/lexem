
# Table of contents

- [Table of contents](#table-of-contents)
- [Methods](#methods)
  - [`.length() -> Integer`](#length---integer)
  - [`.toString() -> String`](#tostring---string)
  - [`.charsAt(...indexes: List<Integer | Interval>) -> String`](#charsatindexes-listinteger--interval---string)
  - [`.charUnicodePointAt(...indexes: List<Integer | Interval>) -> List<Int>`](#charunicodepointatindexes-listinteger--interval---listint)
  - [`.endsWithAny(...suffixes: List<String>) -> Logic`](#endswithanysuffixes-liststring---logic)
  - [`.startsWithAny(...prefixes: List<String>) -> Logic`](#startswithanyprefixes-liststring---logic)
  - [`.containsAny(...substrings: List<String>) -> Logic`](#containsanysubstrings-liststring---logic)
  - [`.containsAll(...substrings: List<String>) -> Logic`](#containsallsubstrings-liststring---logic)
  - [`.indexOf(substring: String) -> Integer | Nil`](#indexofsubstring-string---integer--nil)
  - [`.lastIndexOf(substring: String) -> Integer | Nil`](#lastindexofsubstring-string---integer--nil)
  - [`.padStart(length: Integer, padString: String = " ") -> String`](#padstartlength-integer-padstring-string------string)
  - [`.padEnd(length: Integer, padString: String = " ") -> String`](#padendlength-integer-padstring-string------string)
  - [`.repeat(count: Integer) -> String`](#repeatcount-integer---string)
  - [`.repeat(count: Integer, separator: String) -> String`](#repeatcount-integer-separator-string---string)
  - [`.replace(original: String, replace: String) -> String`](#replaceoriginal-string-replace-string---string)
  - [`.replace(original: String, replace: String, insensible: Logic) -> String`](#replaceoriginal-string-replace-string-insensible-logic---string)
  - [`.slice(from: String) -> String`](#slicefrom-string---string)
  - [`.slice(from: String, count: String) -> String`](#slicefrom-string-count-string---string)
  - [`.split(substring: String) -> List<String>`](#splitsubstring-string---liststring)
  - [`.toLowerCase() -> String`](#tolowercase---string)
  - [`.toUpperCase() -> String`](#touppercase---string)
  - [`.trimStart() -> String`](#trimstart---string)
  - [`.trimEnd() -> String`](#trimend---string)
  - [`.trim() -> String`](#trim---string)
- [Operators](#operators)
  - [`.add(right: Any) -> String`](#addright-any---string)
- [Accesses](#accesses)
  - [`[index: Integer] -> String`](#index-integer---string)

# Methods

## `.length() -> Integer`

Returns the number of characters of the current string.

```lxm
string.length()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `String`.

### Examples

```lxm
let value = "test"

Debug.log(value.length())   -- 4
```

## `.toString() -> String`

Returns the `this` value.

```lxm
string.toString()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `String`.

### Examples

```lxm
let value = "test"

Debug.log(value.toString())               -- "test"
Debug.log(value.toString() === value)     -- true
```

## `.charsAt(...indexes: List<Integer | Interval>) -> String`

Returns the characters at the specified positions.

```lxm
string.charsAt(index1, ..., indexN)
```

### Parameters

- **`indexes`**: the positions of each character.

### Errors

- **`BadArgumentError`**: when the type of any index is not an `Integer` or `Interval`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `String`.

### Examples

```lxm
let value = "this is a test"

Debug.log(value.charsAt(itv![0..3], 8))   -- "testa"
```

## `.charUnicodePointAt(...indexes: List<Integer | Interval>) -> List<Int>`

Returns the _UTF-32_ encoded characters at the specified positions.

```lxm
string.charUTF8At(index1, ..., indexN)
```

### Parameters

- **`indexes`**: the positions of each character.

### Errors

- **`BadArgumentError`**: when the type of any index is not an `Integer` or `Interval`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `String`.

### Examples

```lxm
let value = "this is a test"

Debug.log(value.charUTF8At(itv![0..3], 8))   -- [0x74, 0x68, 0x69, 0x73, 0x61]
```

## `.endsWithAny(...suffixes: List<String>) -> Logic`

Returns a value indicating whether the string ends with any of the specified suffixes.

```lxm
string.endsWithAny(suffix1, ..., suffixN)
```

### Parameters

- **`suffixes`**: the strings to check at the end of the current one.

### Errors

- **`BadArgumentError`**: when the type of any suffix is not a `String`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `String`.

### Examples

```lxm
let value = "this is a test"

Debug.log(value.endsWithAny("test", "s"))     -- true
Debug.log(value.endsWithAny("cc", "st"))      -- true
Debug.log(value.endsWithAny("tc", "xx"))      -- false
```

## `.startsWithAny(...prefixes: List<String>) -> Logic`

Returns a value indicating whether the string ends with any of the specified prefixes.

```lxm
string.startsWithAny(prefix1, ..., prefixN)
```

### Parameters

- **`prefixes`**: the strings to check at the start of the current one.

### Errors

- **`BadArgumentError`**: when the type of any prefix is not a `String`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `String`.

### Examples

```lxm
let value = "this is a test"

Debug.log(value.startsWithAny("this", "s"))   -- true
Debug.log(value.startsWithAny("cc", "th"))    -- true
Debug.log(value.startsWithAny("tc", "xx"))    -- false
```

## `.containsAny(...substrings: List<String>) -> Logic`

Returns a value indicating whether the string contains any of the specified substrings.

```lxm
string.containsAny(substring1, ..., substringN)
```

### Parameters

- **`substrings`**: the strings to check.

### Errors

- **`BadArgumentError`**: when the type of any substring is not a `String`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `String`.

### Examples

```lxm
let value = "this is a test"

Debug.log(value.containsAny("is", "s"))   -- true
Debug.log(value.containsAny("ct", "xx"))  -- false
```

## `.containsAll(...substrings: List<String>) -> Logic`

Returns a value indicating whether the string contains all the specified substrings.

```lxm
string.containsAll(substring1, ..., substringN)
```

### Parameters

- **`substrings`**: the strings to check.

### Errors

- **`BadArgumentError`**: when the type of any substring is not a `String`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `String`.

### Examples

```lxm
let value = "this is a test"

Debug.log(value.containsAll("is", "s"))   -- true
Debug.log(value.containsAll("ct", "xx"))  -- false
```

## `.indexOf(substring: String) -> Integer | Nil`

Returns the first position of the substring inside the current string. In case it is not contained inside the current string, the function returns `nil`.

```lxm
string.indexOf(substring)
```

### Parameters

- **`substring`**: the string to check.

### Errors

- **`BadArgumentError`**: when the type of `substring` is not a `String`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `String`.

### Examples

```lxm
let value = "this is a test and it is cool"

Debug.log(value.indexOf("is"))    -- 5
Debug.log(value.indexOf("ct"))    -- nil
```

## `.lastIndexOf(substring: String) -> Integer | Nil`

Returns the last position of the substring inside the current string. In case it is not contained inside the current string, the function returns `nil`.

```lxm
string.lastIndexOf(substring)
```

### Parameters

- **`substring`**: the string to check.

### Errors

- **`BadArgumentError`**: when the type of `substring` is not a `String`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `String`.

### Examples

```lxm
let value = "this is a test and it is cool"

Debug.log(value.lastIndexOf("is"))    -- 22
Debug.log(value.lastIndexOf("ct"))    -- nil
```

## `.padStart(length: Integer, padString: String = " ") -> String`

Returns the current string if its length is lower or equal than `length`, or the current string preceded by as many `padString` as necessary to reach the specified length.

```lxm
string.padStart(length)
string.padStart(length, padString)
```

### Parameters

- **`length`**: the minimum length to reach.
- **`padString`**: the string to use as padding. It is truncated it it does not fit in the remaining hole.

### Errors

- **`BadArgumentError`**: when any of these conditions do not math.
  - the type of `length` is not an `Integer`.
  - the type of `padString` is not a `String`.
  - `padString` is empty, i.e. equal to `""`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `String`.

### Examples

```lxm
let value = "test"

Debug.log(value.padStart(7))            -- "   test"
Debug.log(value.padStart(7, "12345"))   -- "123test"
Debug.log(value.padStart(7, ""))        -- BadArgumentError
```

## `.padEnd(length: Integer, padString: String = " ") -> String`

Returns the current string if its length is lower or equal than `length`, or the current string followed by as many `padString` as necessary to reach the specified length.

```lxm
string.padEnd(length)
string.padEnd(length, padString)
```

### Parameters

- **`length`**: the minimum length to reach.
- **`padString`**: the string to use as padding. It is truncated it it does not fit in the remaining hole.

### Errors

- **`BadArgumentError`**: when any of these conditions do not math.
  - the type of `length` is not an `Integer`.
  - the type of `padString` is not a `String`.
  - `padString` is empty, i.e. equal to `""`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `String`.

### Examples

```lxm
let value = "test"

Debug.log(value.padEnd(7))            -- "test   "
Debug.log(value.padEnd(7, "12345"))   -- "test123"
Debug.log(value.padEnd(7, ""))        -- BadArgumentError
```

## `.repeat(count: Integer) -> String`

Returns the current string repeated `count` times.

```lxm
string.repeat(count)
```

### Parameters

- **`count`**: the number of times to repeat the string.

### Errors

- **`BadArgumentError`**: when the type of `count` is not an `Integer` or it is lower than 0.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `String`.

### Examples

```lxm
let value = "test"

Debug.log(value.repeat(0))    -- ""
Debug.log(value.repeat(1))    -- "test"
Debug.log(value.repeat(3))    -- "testtesttest"
Debug.log(value.repeat(-1))   -- BadArgumentError
```

## `.repeat(count: Integer, separator: String) -> String`

Returns the current string repeated `count` times separating each repetition with `separator`.

```lxm
string.repeat(count, separator)
```

### Parameters

- **`count`**: the number of times to repeat the string.
- **`separator`**: the string that separate the repetitions.

### Errors

- **`BadArgumentError`**: when any of these conditions do not math.
  - the type of `count` is not an `Integer`.
  - the type of `separator` is not a `String`.
  - `count` is lower than 0.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `String`.

### Examples

```lxm
let value = "test"

Debug.log(value.repeat(0, ", "))    -- ""
Debug.log(value.repeat(1, ", "))    -- "test"
Debug.log(value.repeat(3, ", "))    -- "test, test, test"
Debug.log(value.repeat(-1, ", "))   -- BadArgumentError
```

## `.replace(original: String, replace: String) -> String`

Returns the current string with all the occurrences of the `original` replaced by `replace`.

```lxm
string.replace(original, replace)
```

### Parameters

- **`original`**: the string to replace.
- **`replace`**: the string that will replace the original.

### Errors

- **`BadArgumentError`**: when any of these conditions do not math.
  - the type of `original` is not a `String`.
  - the type of `replace` is not a `String`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `String`.

### Examples

```lxm
let value = "aa bb cc dd"

Debug.log(value.replace("bb", "xx"))  -- "aa xx cc dd"
Debug.log(value.replace("ll", "xx"))  -- "aa bb cc dd"
Debug.log(value.replace(nil, ", "))   -- BadArgumentError
```

## `.replace(original: String, replace: String, insensible: Logic) -> String`

Returns the current string with all the occurrences of the `original` replaced by `replace`.

```lxm
string.replace(original, replace)
```

### Parameters

- **`original`**: the string to replace.
- **`replace`**: the string that will replace the original.
- **`insensible`**: whether to treat uppercase and lowercase characters indistinctly.

### Errors

- **`BadArgumentError`**: when any of these conditions do not math.
  - the type of `original` is not a `String`.
  - the type of `replace` is not a `String`.
  - the type of `insensible` is not a `Logic`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `String`.

### Examples

```lxm
let value = "aA Bb CC dd"

Debug.log(value.replace("bb", "XX", true))    -- "aA XX CC dd"
Debug.log(value.replace("cC", "xx", false))   -- "aA Bb CC dd"
Debug.log(value.replace(nil, ", "))           -- BadArgumentError
```

## `.slice(from: String) -> String`

Returns the substring of the current string that starts at `from` and finishes at the end of the current string. If `from` is greater than the size of the current string, the function returns an empty string, i.e. `""`.

```lxm
string.slice(from)
```

### Parameters

- **`from`**: the start index of the substring.

### Errors

- **`BadArgumentError`**: when the type of `from` is not an `Integer` or it is lower than 0.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `String`.

### Examples

```lxm
let value = "this is a test"

Debug.log(value.slice(5))     -- "is a test"
Debug.log(value.slice(20))    -- ""
Debug.log(value.slice(nil))   -- BadArgumentError
```

## `.slice(from: String, count: String) -> String`

Returns the substring of the current string that starts at `from` and ends at most in the following `count` characters. If `from` is greater than the size of the current string, the function returns an empty string, i.e. `""`.

```lxm
string.slice(from, count)
```

### Parameters

- **`from`**: the start index of the substring.
- **`count`**: the maximum number of characters of the substring.

### Errors

- **`BadArgumentError`**: when any of these conditions do not math.
  - the type of `from` is not an `Integer`.
  - the type of `count` is not an `Integer`.
  - `from` is lower than 0.
  - `count` is lower than 0.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `String`.

### Examples

```lxm
let value = "this is a test"

Debug.log(value.slice(5, 4))        -- "is a"
Debug.log(value.slice(10, 10))      -- "test"
Debug.log(value.slice(20, 10))      -- ""
Debug.log(value.slice(nil, ""))     -- BadArgumentError
```

## `.split(substring: String) -> List<String>`

Splits the current string into a list of strings by separating it by the specified substring.

```lxm
string.split(substring)
```

### Parameters

- **`substring`**: the string that act as separator.

### Errors

- **`BadArgumentError`**: when the type of `substring` is not a `String`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `String`.

### Examples

```lxm
let value = "this, is, a, test"

Debug.log(value.split(","))    -- ["this", " is", " a", " test"]
```

## `.toLowerCase() -> String`

Returns the string with all its characters lowercase.

```lxm
string.toLowerCase()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `String`.

### Examples

```lxm
let value = "This IS a TeSt"

Debug.log(value.toLowerCase())    -- "this is a test"
```

## `.toUpperCase() -> String`

Returns the string with all its characters uppercase.

```lxm
string.toUpperCase()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `String`.

### Examples

```lxm
let value = "This IS a TeSt"

Debug.log(value.toUpperCase())    -- "THIS IS A TEST"
```

## `.trimStart() -> String`

Returns the string without any whitespace at the beginning of it.

```lxm
string.trimStart()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `String`.

### Examples

```lxm
let value = "   this is a test   "

Debug.log(value.trimStart())    -- "this is a test   "
```

## `.trimEnd() -> String`

Returns the string without any whitespace at the end of it.

```lxm
string.trimEnd()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `String`.

### Examples

```lxm
let value = "   this is a test   "

Debug.log(value.trimEnd())    -- "   this is a test"
```

## `.trim() -> String`

Returns the string without any whitespace at both sides of it.

```lxm
string.trim()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `String`.

### Examples

```lxm
let value = "   this is a test   "

Debug.log(value.trim())    -- "this is a test"
```

# Operators

## `.add(right: Any) -> String`

Returns the concatenation of the `this` value to the string representation of the `right` value, i.e `this + right.toString()`.

```lxm
string.add(right)
```

### Parameters

- **`right`**: the right operand.

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not an `String`.

### Examples

```lxm
let left = "test "
let right = 4

Debug.log(left.add(right))    -- 4
Debug.log(left.add(nil))      -- BadArgumentError
Debug.log(left + right)       -- 4 Implicit calling
```

# Accesses

## `[index: Integer] -> String`

Returns the character at the specified position.

```lxm
string[index]
```

### Parameters

- **`index`**: the position of the cell.

### Errors

- **`BadArgumentError`**: when the type of `index` is not an `Integer`.
- **`IndexOutOfBounds`**: when the `index` greater than the last valid index.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `String`.

### Examples

```lxm
let string = "test"

Debug.log(string[nil])    -- BadArgumentError
Debug.log(string[0])      -- "t"
Debug.log(string[1])      -- "e"
Debug.log(string[2])      -- "s"
Debug.log(string[3])      -- "t"
```
