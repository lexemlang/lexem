
# Table of contents

- [Table of contents](#table-of-contents)
- [Methods](#methods)
  - [`.toString() -> String`](#tostring---string)
  - [`.toString(radix: Integer) -> String`](#tostringradix-integer---string)
- [Operators](#operators)
  - [`.negate() -> Integer`](#negate---integer)
  - [`.affirm() -> Integer`](#affirm---integer)
  - [`.multiply(right: Integer | Float) -> Integer | Float`](#multiplyright-integer--float---integer-float)
  - [`.divide(right: Integer | Float) -> Integer | Float`](#divideright-integer--float---integer-float)
  - [`.intDivide(right: Integer | Float) -> Integer`](#intdivideright-integer--float---integer)
  - [`.reminder(right: Integer | Float) -> Integer | Float`](#reminderright-integer--float---integer-float)
  - [`.add(right: Integer | Float) -> Integer | Float`](#addright-integer--float---integer-float)
  - [`.sub(right: Integer | Float) -> Integer | Float`](#subright-integer--float---integer-float)

# Methods

## `.toString() -> String`

Returns a `String` representing the given number.

```lxm
integer.toString()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not an `Integer`.

### Examples

```lxm
let num = 450

log(num.toString())     -- "450"
```

## `.toString(radix: Integer) -> String`

Returns a `String` representing the given number in the specified radix `radix`.

```lxm
integer.toString(radix)
```

### Parameters

- **`radix`**: the radix of the resulting number. Only valid: 2, 8, 10 or 16.

### Errors

- **`BadArgumentError`**: when `radix` is not one of 2, 8, 10 or 16.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not an `Integer`.

### Examples

```lxm
let num = 21

log(num.toString())     -- BadArgumentError
log(num.toString(2))    -- "10101"
log(num.toString(8))    -- "25"
log(num.toString(10))   -- "21"
log(num.toString(16))   -- "15"
```

# Operators

## `.negate() -> Integer`

Returns the negation of the `this` value, i.e `-this`.

```lxm
integer.negate()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not an `Integer`.

### Examples

```lxm
let value = 3

log(value.negate()) -- -3
log(-value)         -- -3 Implicit calling
```

## `.affirm() -> Integer`

Returns the negation of the `this` value, i.e `+this`.

```lxm
integer.affirm()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not an `Integer`.

### Examples

```lxm
let value = 3

log(value.affirm())  -- 3
log(+value)             -- 3 Implicit calling
```

## `.multiply(right: Integer | Float) -> Integer | Float`

Returns the multiplication of the `this` value `right` times, i.e `this * right`.

```lxm
integer.multiply(right)
```

### Parameters

- **`right`**: the right operand.

### Errors

- **`BadArgumentError`**: when the type of `right` is incorrect.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not an `Integer`.

### Examples

```lxm
let left = 3
let rightInt = 4
let rightFloat = 5.2

log(left.multiply(rightInt))    -- 12
log(left.multiply(rightFloat))  -- 15.6
log(left.multiply(nil))         -- BadArgumentError
log(left * rightInt)            -- 12 Implicit calling
```

## `.divide(right: Integer | Float) -> Integer | Float`

Returns the division of the `this` value by the `right` value, i.e `this / right`.

```lxm
integer.divide(right)
```

### Parameters

- **`right`**: the right operand.

### Errors

- **`BadArgumentError`**: when the type of `right` is incorrect.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not an `Integer`.

### Examples

```lxm
let left = 3
let rightInt = 2
let rightFloat = 1.5

log(left.divide(rightInt))    -- 1
log(left.divide(rightFloat))  -- 2.0
log(left.divide(nil))         -- BadArgumentError
log(left / rightInt)          -- 1 Implicit calling
```

## `.intDivide(right: Integer | Float) -> Integer`

Returns the integer division of the `this` value by the `right` value, i.e `this // right`.

```lxm
integer.intDivide(right)
```

### Parameters

- **`right`**: the right operand.

### Errors

- **`BadArgumentError`**: when the type of `right` is incorrect.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not an `Integer`.

### Examples

```lxm
let left = 3
let rightInt = 2
let rightFloat = 1.5

log(left.intDivide(rightInt))   -- 1
log(left.intDivide(rightFloat)) -- 2
log(left.intDivide(nil))        -- BadArgumentError
log(left // rightInt)           -- 1 Implicit calling
```

## `.reminder(right: Integer | Float) -> Integer | Float`

Returns the remainder of the division of the `this` value by the `right` value, i.e `this % right`.

```lxm
integer.reminder(right)
```

### Parameters

- **`right`**: the right operand.

### Errors

- **`BadArgumentError`**: when the type of `right` is incorrect.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not an `Integer`.

### Examples

```lxm
let left = 3.0
let rightInt = 2
let rightFloat = 1.4

log(left.reminder(rightInt))   -- 1
log(left.reminder(rightFloat)) -- 0.2
log(left.reminder(nil))        -- BadArgumentError
log(left % rightInt)           -- 1 Implicit calling
```

## `.add(right: Integer | Float) -> Integer | Float`

Returns the addition of the `this` value to the `right` value, i.e `this + right`.

```lxm
integer.add(right)
```

### Parameters

- **`right`**: the right operand.

### Errors

- **`BadArgumentError`**: when the type of `right` is incorrect.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not an `Integer`.

### Examples

```lxm
let left = 3
let rightInt = 4
let rightFloat = 5.2

log(left.add(rightInt))   -- 7
log(left.add(rightFloat)) -- 8.2
log(left.add(nil))        -- BadArgumentError
log(left + rightInt)      -- 7 Implicit calling
```

## `.sub(right: Integer | Float) -> Integer | Float`

Returns the subtraction of the `right` value from the `this` value, i.e `this - right`.

```lxm
integer.add(right)
```

### Parameters

- **`right`**: the right operand.

### Errors

- **`BadArgumentError`**: when the type of `right` is incorrect.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not an `Integer`.

### Examples

```lxm
let left = 3
let rightInt = 2
let rightFloat = 5.2

log(left.sub(rightInt))   -- 1
log(left.sub(rightFloat)) -- -2.2
log(left.sub(nil))        -- BadArgumentError
log(left - rightInt)      -- 1 Implicit calling
```
