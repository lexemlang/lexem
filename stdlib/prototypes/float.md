
# Table of contents

- [Table of contents](#table-of-contents)
- [Methods](#methods)
  - [`.integerPart() -> Integer`](#integerpart---integer)
    - [Errors](#errors)
    - [Examples](#examples)
  - [`.decimalPart() -> Float`](#decimalpart---float)
    - [Errors](#errors-1)
    - [Examples](#examples-1)
  - [`.toExponential(precision: Integer?) -> String`](#toexponentialprecision-integer---string)
    - [Parameters](#parameters)
    - [Errors](#errors-2)
    - [Examples](#examples-2)
  - [`.toFixed(precision: Integer) -> String`](#tofixedprecision-integer---string)
    - [Parameters](#parameters-1)
    - [Errors](#errors-3)
    - [Examples](#examples-3)
  - [`.toString() -> String`](#tostring---string)
    - [Errors](#errors-4)
    - [Examples](#examples-4)
  - [`.toString(radix: Integer) -> String`](#tostringradix-integer---string)
    - [Parameters](#parameters-2)
    - [Errors](#errors-5)
    - [Examples](#examples-5)
- [Operators](#operators)
  - [`.negate() -> Float`](#negate---float)
    - [Errors](#errors-6)
    - [Examples](#examples-6)
  - [`.affirmate() -> Integer`](#affirmate---integer)
    - [Errors](#errors-7)
    - [Examples](#examples-7)
  - [`.multiply(right: Integer | Float) -> Float`](#multiplyright-integer--float---float)
    - [Parameters](#parameters-3)
    - [Errors](#errors-8)
    - [Examples](#examples-8)
  - [`.divide(right: Integer | Float) -> Float`](#divideright-integer--float---float)
    - [Parameters](#parameters-4)
    - [Errors](#errors-9)
    - [Examples](#examples-9)
  - [`.intDivide(right: Integer | Float) -> Integer`](#intdivideright-integer--float---integer)
    - [Parameters](#parameters-5)
    - [Errors](#errors-10)
    - [Examples](#examples-10)
  - [`.reminder(right: Integer | Float) -> Float`](#reminderright-integer--float---float)
    - [Parameters](#parameters-6)
    - [Errors](#errors-11)
    - [Examples](#examples-11)
  - [`.add(right: Integer | Float) -> Float`](#addright-integer--float---float)
    - [Parameters](#parameters-7)
    - [Errors](#errors-12)
    - [Examples](#examples-12)
  - [`.sub(right: Integer | Float) -> Float`](#subright-integer--float---float)
    - [Parameters](#parameters-8)
    - [Errors](#errors-13)
    - [Examples](#examples-13)

# Methods

## `.integerPart() -> Integer`

Returns an `Integer` which is the integer part of the number.

```lxm
float.integerPart()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Float`.

### Examples

```lxm
let num = 450.73

log(num.integerPart())  -- 450
```

## `.decimalPart() -> Float`

Returns a new `Float` which is the integer part of the number.

```lxm
float.decimalPart()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Float`.

### Examples

```lxm
let num = 450.73

log(num.decimalPart())  -- 0.73
```

## `.toExponential(precision: Integer?) -> String`

Returns a `String` representing the given number in exponential notation with one digit before the decimal point and the specified number.

```lxm
float.toExponential()
float.toExponential(precision)
```

### Parameters

- **`precision`**: the number of digits after the decimal point.
  - `default`: as many digits as necessary to specify the number.

### Errors

- **`BadArgumentError`**: when `precision` is not a positive `Integer` or `nil`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Float`.

### Examples

```lxm
let num = 450.7

log(num.toExponential())    -- 4.507e+2
log(num.toExponential(0))   -- 5e+2
log(num.toExponential(1))   -- 4.5e+2
log(num.toExponential(-1))  -- BadArgumentError
```

## `.toFixed(precision: Integer) -> String`

Returns a `String` representing the given number in a fixed-point notation specified by `precision`.

```lxm
float.toFixed(precision)
```

### Parameters

- **`precision`**: the number of digits after the decimal point.

### Errors

- **`BadArgumentError`**: when `precision` is not a positive `Integer`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Float`.

### Examples

```lxm
let num = 450.73

log(num.toFixed())      -- BadArgumentError
log(num.toFixed(0))     -- 451
log(num.toFixed(1))     -- 450.7
log(num.toFixed(-1))    -- BadArgumentError
```

## `.toString() -> String`

Returns a `String` representing the given number.

```lxm
float.toString()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Float`.

### Examples

```lxm
let num = 450.73

log(num.toString())     -- "450.73"
```

## `.toString(radix: Integer) -> String`

Returns a `String` representing the given number in the specified radix `radix`.

```lxm
float.toString(radix)
```

### Parameters

- **`radix`**: the radix of the resulting number. Only valid: 2, 8, 10 or 16.

### Errors

- **`BadArgumentError`**: when `radix` is not one of 2, 8, 10 or 16.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Float`.

### Examples

```lxm
let num = 21.125

log(num.toString())     -- BadArgumentError
log(num.toString(2))    -- "10101.001"
log(num.toString(8))    -- "25.1"
log(num.toString(10))   -- "21.125"
log(num.toString(16))   -- "15.2"
```

# Operators

## `.negate() -> Float`

Returns the negation of the `this` value, i.e `-this`.

```lxm
float.negate()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Float`.

### Examples

```lxm
let value = 3.0

log(value.negate()) -- -3.0
log(-value)         -- -3.0 Implicit calling
```

## `.affirmate() -> Integer`

Returns the negation of the `this` value, i.e `+this`.

```lxm
integer.affirmate()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not an `Integer`.

### Examples

```lxm
let value = 3

log(value.affirmate())  -- 3
log(+value)             -- 3 Implicit calling
```

## `.multiply(right: Integer | Float) -> Float`

Returns the multiplication of the `this` value `right` times, i.e `this * right`.

```lxm
float.multiply(right)
```

### Parameters

- **`right`**: the right operand.

### Errors

- **`BadArgumentError`**: when the type of `right` is incorrect.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Float`.

### Examples

```lxm
let left = 3.0
let rightInt = 4
let rightFloat = 5.2

log(left.multiply(rightInt))    -- 12.0
log(left.multiply(rightFloat))  -- 15.6
log(left.multiply(nil))         -- BadArgumentError
log(left * rightInt)            -- 12.0 Implicit calling
```

## `.divide(right: Integer | Float) -> Float`

Returns the division of the `this` value by the `right` value, i.e `this / right`.

```lxm
float.divide(right)
```

### Parameters

- **`right`**: the right operand.

### Errors

- **`BadArgumentError`**: when the type of `right` is incorrect.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Float`.

### Examples

```lxm
let left = 3.0
let rightInt = 2
let rightFloat = 1.5

log(left.divide(rightInt))    -- 1.5
log(left.divide(rightFloat))  -- 2.0
log(left.divide(nil))         -- BadArgumentError
log(left / rightInt)          -- 1.5 Implicit calling
```

## `.intDivide(right: Integer | Float) -> Integer`

Returns the integer division of the `this` value by the `right` value, i.e `this // right`.

```lxm
float.intDivide(right)
```

### Parameters

- **`right`**: the right operand.

### Errors

- **`BadArgumentError`**: when the type of `right` is incorrect.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Float`.

### Examples

```lxm
let left = 3.0
let rightInt = 2
let rightFloat = 1.5

log(left.intDivide(rightInt))   -- 1
log(left.intDivide(rightFloat)) -- 2
log(left.intDivide(nil))        -- BadArgumentError
log(left // rightInt)           -- 1 Implicit calling
```

## `.reminder(right: Integer | Float) -> Float`

Returns the remainder of the division of the `this` value by the `right` value, i.e `this % right`.

```lxm
float.reminder(right)
```

### Parameters

- **`right`**: the right operand.

### Errors

- **`BadArgumentError`**: when the type of `right` is incorrect.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Float`.

### Examples

```lxm
let left = 3.0
let rightInt = 2
let rightFloat = 1.4

log(left.reminder(rightInt))   -- 1.0
log(left.reminder(rightFloat)) -- 0.2
log(left.reminder(nil))        -- BadArgumentError
log(left % rightInt)           -- 1.0 Implicit calling
```

## `.add(right: Integer | Float) -> Float`

Returns the addition of the `this` value to the `right` value, i.e `this + right`.

```lxm
float.add(right)
```

### Parameters

- **`right`**: the right operand.

### Errors

- **`BadArgumentError`**: when the type of `right` is incorrect.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Float`.

### Examples

```lxm
let left = 3.0
let rightInt = 4
let rightFloat = 5.2

log(left.add(rightInt))   -- 7.0
log(left.add(rightFloat)) -- 8.2
log(left.add(nil))        -- BadArgumentError
log(left + rightInt)      -- 7.0 Implicit calling
```

## `.sub(right: Integer | Float) -> Float`

Returns the subtraction of the `right` value from the `this` value, i.e `this - right`.

```lxm
float.add(right)
```

### Parameters

- **`right`**: the right operand.

### Errors

- **`BadArgumentError`**: when the type of `right` is incorrect.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Float`.

### Examples

```lxm
let left = 3.0
let rightInt = 2
let rightFloat = 5.2

log(left.sub(rightInt))   -- 1.0
log(left.sub(rightFloat)) -- -2.2
log(left.sub(nil))        -- BadArgumentError
log(left - rightInt)      -- 1.0 Implicit calling
```
