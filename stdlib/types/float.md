
# Table of contents

- [Table of contents](#table-of-contents)
- [Methods](#methods)
  - [`.parse(value: String) -> Float | Nil`](#parsevalue-string---float--nil)
  - [`.parse(value: String, radix: Integer) -> Float | Nil`](#parsevalue-string-radix-integer---float--nil)
  - [`.epsilonEquals(left: Float | Integer, right: Float | Integer) -> Logic`](#epsilonequalsleft-float-integer-right-float-integer---logic)
- [Properties](#properties)
  - [`.prototype -> Object`](#prototype---object)
  - [`.Infinity -> Object`](#infinity---object)
  - [`.Epsilon -> Object`](#epsilon---object)
  - [`.MinValue -> Object`](#minvalue---object)
  - [`.MinPositiveValue -> Object`](#minpositivevalue---object)
  - [`.MaxValue -> Object`](#maxvalue---object)

# Methods

## `.parse(value: String) -> Float | Nil`

Returns a `Float` value equivalent to the specified string representation. This method searches for one of the available number prefixes (`"0b"`, `"0o"`, `"0d"` and `"0x"`) to get the radix of the number or defaults to 10 if it is not present. The function returns `nil` if it can not parse the `value`.

```lxm
Float.parse(value)
```

### Parameters

- **`value`**: the string representation of the number.

### Errors

- **`BadArgumentError`**: when `value` is not a `String`.

### Examples

```lxm
Debug.log(Float.parse("0b10101.001"))   -- 21.125
Debug.log(Float.parse("0o25.1"))        -- 21.125
Debug.log(Float.parse("0d21.125"))      -- 21.125
Debug.log(Float.parse("0x15.2"))        -- 21.125
Debug.log(Float.parse("21.125"))        -- 21.125
Debug.log(Float.parse(nil))             -- BadArgumentError
```

## `.parse(value: String, radix: Integer) -> Float | Nil`

Returns a `Float` value equivalent to the specified string representation written in the specified radix. The function returns `nil` if it can not parse the `value`.

```lxm
Float.parse(value, radix)
```

### Parameters

- **`value`**: the string representation of the number.
- **`radix`**: the radix in which the number is represented in the string.

### Errors

- **`BadArgumentError`**: when any of these conditions do not math.
  - the type of `value` is not a `String`.
  - `radix` is not one of 2, 8, 10 or 16.

### Examples

```lxm
Debug.log(Float.parse("10101.001", 2))  -- 21.125
Debug.log(Float.parse("25.1", 8))       -- 21.125
Debug.log(Float.parse("21.125", 10))    -- 21.125
Debug.log(Float.parse("15.2", 16))      -- 21.125
Debug.log(Float.parse(nil))             -- BadArgumentError
```

## `.epsilonEquals(left: Float | Integer, right: Float | Integer) -> Logic`

Returns whether both numbers are epsilon-relatively equals, i.e. that the following condition succeeds `Math.abs(left - right) <= Float.Epsilon`.

```lxm
Float.epsilonEquals(value, radix)
```

### Parameters

- **`left`**: the left operand.
- **`right`**: the right operand.

### Errors

- **`BadArgumentError`**: when any of the operands are not of type `Float` nor `Integer`.

### Examples

```lxm
Debug.log(Float.epsilonEquals(2.1, 3))                  -- false
Debug.log(Float.epsilonEquals(2, 2 + Float.Empsilon))   -- true
Debug.log(Float.epsilonEquals(nil, ""))                 -- BadArgumentError
```

# Properties

## `.prototype -> Object`

The prototype of the type.

```lxm
Float.prototype
```

## `.Infinity -> Object`

The Infinity representation.

```lxm
Float.Infinity
```

## `.Epsilon -> Object`

Represents the difference between 1 and the smallest floating point number greater than 1.

```lxm
Float.Epsilon
```

## `.MinValue -> Object`

The minimum available value that can be represented in a `Float`.

```lxm
Float.MinValue
```

## `.MinPositiveValue -> Object`

The minimum positive value that can be represented in a `Float`.

```lxm
Float.MinValue
```

## `.MaxValue -> Object`

The maximum available value that can be represented in a `Float`.

```lxm
Float.MaxValue
```
