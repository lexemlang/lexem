
# Table of contents

- [Table of contents](#table-of-contents)
- [Methods](#methods)
  - [.integerPart() -&gt; Integer](#integerpart--gt-integer)
  - [.decimalPart() -&gt; Float](#decimalpart--gt-float)
  - [.toExponential(precision: Integer?) -&gt; String](#toexponentialprecision-integer--gt-string)
  - [.toFixed(precision: Integer) -&gt; String](#tofixedprecision-integer--gt-string)
  - [.toString() -&gt; String](#tostring--gt-string)
  - [.toString(radix: Integer) -&gt; String](#tostringradix-integer--gt-string)
- [Operators](#operators)
  - [.negate() -&gt; Float](#negate--gt-float)
  - [.affirm() -&gt; Float](#affirm--gt-float)
  - [.multiply(right: Integer | Float) -&gt; Float](#multiplyright-integer--float--gt-float)
  - [.divide(right: Integer | Float) -&gt; Float](#divideright-integer--float--gt-float)
  - [.intDivide(right: Integer | Float) -&gt; Integer](#intdivideright-integer--float--gt-integer)
  - [.reminder(right: Integer | Float) -&gt; Float](#reminderright-integer--float--gt-float)
  - [.add(right: Integer | Float) -&gt; Float](#addright-integer--float--gt-float)
  - [.sub(right: Integer | Float) -&gt; Float](#subright-integer--float--gt-float)

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

Debug.log(num.integerPart())  -- 450
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

Debug.log(num.decimalPart())  -- 0.73
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

Debug.log(num.toExponential())    -- 4.507e+2
Debug.log(num.toExponential(0))   -- 5e+2
Debug.log(num.toExponential(1))   -- 4.5e+2
Debug.log(num.toExponential(-1))  -- BadArgumentError
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

Debug.log(num.toFixed())      -- BadArgumentError
Debug.log(num.toFixed(0))     -- 451
Debug.log(num.toFixed(1))     -- 450.7
Debug.log(num.toFixed(-1))    -- BadArgumentError
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

Debug.log(num.toString())     -- "450.73"
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

Debug.log(num.toString())     -- BadArgumentError
Debug.log(num.toString(2))    -- "10101.001"
Debug.log(num.toString(8))    -- "25.1"
Debug.log(num.toString(10))   -- "21.125"
Debug.log(num.toString(16))   -- "15.2"
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

Debug.log(value.negate()) -- -3.0
Debug.log(-value)         -- -3.0 Implicit calling
```

## `.affirm() -> Float`

Returns the negation of the `this` value, i.e `+this`.

```lxm
float.affirm()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not an `Integer`.

### Examples

```lxm
let value = 3.0

Debug.log(value.affirm())   -- 3.0
Debug.log(+value)           -- 3.0 Implicit calling
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

Debug.log(left.multiply(rightInt))    -- 12.0
Debug.log(left.multiply(rightFloat))  -- 15.6
Debug.log(left.multiply(nil))         -- BadArgumentError
Debug.log(left * rightInt)            -- 12.0 Implicit calling
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

Debug.log(left.divide(rightInt))    -- 1.5
Debug.log(left.divide(rightFloat))  -- 2.0
Debug.log(left.divide(nil))         -- BadArgumentError
Debug.log(left / rightInt)          -- 1.5 Implicit calling
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

Debug.log(left.intDivide(rightInt))   -- 1
Debug.log(left.intDivide(rightFloat)) -- 2
Debug.log(left.intDivide(nil))        -- BadArgumentError
Debug.log(left // rightInt)           -- 1 Implicit calling
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

Debug.log(left.reminder(rightInt))   -- 1.0
Debug.log(left.reminder(rightFloat)) -- 0.2
Debug.log(left.reminder(nil))        -- BadArgumentError
Debug.log(left % rightInt)           -- 1.0 Implicit calling
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

Debug.log(left.add(rightInt))   -- 7.0
Debug.log(left.add(rightFloat)) -- 8.2
Debug.log(left.add(nil))        -- BadArgumentError
Debug.log(left + rightInt)      -- 7.0 Implicit calling
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

Debug.log(left.sub(rightInt))   -- 1.0
Debug.log(left.sub(rightFloat)) -- -2.2
Debug.log(left.sub(nil))        -- BadArgumentError
Debug.log(left - rightInt)      -- 1.0 Implicit calling
```
