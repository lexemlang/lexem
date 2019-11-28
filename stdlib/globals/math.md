
# Table of contents

- [Table of contents](#table-of-contents)
- [Methods](#methods)
  - [`.abs(number: Integer | Float) -> Integer | Float`](#absnumber-integer--float---integer--float)
  - [`.acos(number: Integer | Float) -> Float | Nil`](#acosnumber-integer--float---float--nil)
  - [`.acosh(number: Integer | Float) -> Float | Nil`](#acoshnumber-integer--float---float--nil)
  - [`.asin(number: Integer | Float) -> Float | Nil`](#asinnumber-integer--float---float--nil)
  - [`.asinh(number: Integer | Float) -> Float`](#asinhnumber-integer--float---float)
  - [`.atan(number: Integer | Float) -> Float`](#atannumber-integer--float---float)
  - [`.atanh(number: Integer | Float) -> Float | Nil`](#atanhnumber-integer--float---float--nil)
  - [`.atan2(x: Integer | Float, y: Integer | Float) -> Float`](#atan2x-integer--float-y-integer--float---float)
  - [`.cbrt(number: Integer | Float) -> Float`](#cbrtnumber-integer--float---float)
  - [`.ceil(number: Integer | Float) -> Integer`](#ceilnumber-integer--float---integer)
  - [`.clz32(number: Integer) -> Integer`](#clz32number-integer---integer)
  - [`.cos(number: Integer | Float) -> Float`](#cosnumber-integer--float---float)
  - [`.cosh(number: Integer | Float) -> Float`](#coshnumber-integer--float---float)
  - [`.exp(number: Integer | Float) -> Float`](#expnumber-integer--float---float)
  - [`.floor(number: Integer | Float) -> Integer`](#floornumber-integer--float---integer)
  - [`.hypot(...numbers: List<Integer | Float>) -> Float`](#hypotnumbers-listinteger--float---float)
  - [`.ln(number: Integer | Float) -> Float`](#lnnumber-integer--float---float)
  - [`.log10(number: Integer | Float) -> Float`](#log10number-integer--float---float)
  - [`.log2(number: Integer | Float) -> Float`](#log2number-integer--float---float)
  - [`.max(...numbers: List<Integer | Float>) -> Float`](#maxnumbers-listinteger--float---float)
  - [`.min(...numbers: List<Integer | Float>) -> Float`](#minnumbers-listinteger--float---float)
  - [`.pow(base: Integer | Float, exponent: Integer | Float) -> Float | Nil`](#powbase-integer--float-exponent-integer--float---float--nil)
  - [`.random() -> Float`](#random---float)
  - [`.round(number: Integer | Float) -> Integer`](#roundnumber-integer--float---integer)
  - [`.sign(number: Integer | Float) -> Integer`](#signnumber-integer--float---integer)
  - [`.sin(number: Integer | Float) -> Float`](#sinnumber-integer--float---float)
  - [`.sinh(number: Integer | Float) -> Float`](#sinhnumber-integer--float---float)
  - [`.sqrt(number: Integer | Float) -> Float | Nil`](#sqrtnumber-integer--float---float-nil)
  - [`.tan(number: Integer | Float) -> Float`](#tannumber-integer--float---float)
  - [`.tanh(number: Integer | Float) -> Float`](#tanhnumber-integer--float---float)
  - [`.trunc(number: Integer | Float) -> Integer`](#truncnumber-integer--float---integer)
- [Properties](#properties)
  - [`.E -> Float`](#e---float)
  - [`.LN2 -> Float`](#ln2---float)
  - [`.LN10 -> Float`](#ln10---float)
  - [`.LOG10_E -> Float`](#log10_e---float)
  - [`.LOG10_2 -> Float`](#log10_2---float)
  - [`.LOG2_E -> Float`](#log2_e---float)
  - [`.LOG2_10 -> Float`](#log2_10---float)
  - [`.PI -> Float`](#pi---float)
  - [`.SQRT1_2 -> Float`](#sqrt1_2---float)
  - [`.SQRT2 -> Float`](#sqrt2---float)
  - [`.RAD2DEG -> Float`](#rad2deg---float)
  - [`.DEG2RAD -> Float`](#deg2rad---float)

# Methods

## `.abs(number: Integer | Float) -> Integer | Float`

Returns the absolute value of the specified number.

```lxm
Math.abs(number)
```

### Parameters

- **`number`**: the number to operate with.

### Errors

- **`BadArgumentError`**: when `number` is not an `Integer` or `Float`.

### Examples

```lxm
Debug.log(Math.abs(4))        -- 4
Debug.log(Math.abs(-1.5))     -- 1.5
```

## `.acos(number: Integer | Float) -> Float | Nil`

Returns the arc-cosine of the specified number. The function returns `nil` if the number is outside the range [-1, 1].

```lxm
Math.acos(number)
```

### Parameters

- **`number`**: the number to operate with. It must be in radians.

### Errors

- **`BadArgumentError`**: when `number` is not an `Integer` or `Float`.

### Examples

```lxm
Debug.log(Math.acos(-2))      -- nil
Debug.log(Math.acos(0))       -- 1.5707963267948966
Debug.log(Math.acos(0.5))     -- 1.0471975511965979
```

## `.acosh(number: Integer | Float) -> Float | Nil`

Returns the hyperbolic arc-cosine of the specified number. The function returns `nil` if the number is lower than 1.

```lxm
Math.acosh(number)
```

### Parameters

- **`number`**: the number to operate with. It must be in radians.

### Errors

- **`BadArgumentError`**: when `number` is not an `Integer` or `Float`.

### Examples

```lxm
Debug.log(Math.acosh())       -- nil
Debug.log(Math.acosh(1))      -- 0.0
Debug.log(Math.acosh(1.5))    -- 0.9624236501192069
```

## `.asin(number: Integer | Float) -> Float | Nil`

Returns the arc-sine of the specified number. The function returns `nil` if the number is outside the range [-1, 1].

```lxm
Math.asin(number)
```

### Parameters

- **`number`**: the number to operate with. It must be in radians.

### Errors

- **`BadArgumentError`**: when `number` is not an `Integer` or `Float`.

### Examples

```lxm
Debug.log(Math.asin(0))       -- 0.0
Debug.log(Math.asin(0.5))     -- 0.5235987755982989
Debug.log(Math.asin(2))       -- nil
```

## `.asinh(number: Integer | Float) -> Float`

Returns the hyperbolic arc-sine of the specified number.

```lxm
Math.asinh(number)
```

### Parameters

- **`number`**: the number to operate with. It must be in radians.

### Errors

- **`BadArgumentError`**: when `number` is not an `Integer` or `Float`.

### Examples

```lxm
Debug.log(Math.asinh(1))       -- 0.881373587019543
Debug.log(Math.asinh(1.5))     -- 1.1947632172871094
```

## `.atan(number: Integer | Float) -> Float`

Returns the arc-tangent of the specified number.

```lxm
Math.atan(number)
```

### Parameters

- **`number`**: the number to operate with. It must be in radians.

### Errors

- **`BadArgumentError`**: when `number` is not an `Integer` or `Float`.

### Examples

```lxm
Debug.log(Math.atan(0))       -- 0.0
Debug.log(Math.atan(0.5))     -- 0.4636476090008061
```

## `.atanh(number: Integer | Float) -> Float | Nil`

Returns the hyperbolic arc-tangent of the specified number. The function returns `nil` if the number is outside the range [-1, 1].

```lxm
Math.atanh(number)
```

### Parameters

- **`number`**: the number to operate with. It must be in radians.

### Errors

- **`BadArgumentError`**: when `number` is not an `Integer` or `Float`.

### Examples

```lxm
Debug.log(Math.atanh(0))       -- 0.0
Debug.log(Math.atanh(0.5))     -- 0.5493061443340548
Debug.log(Math.atanh(2))       -- nil
```

## `.atan2(x: Integer | Float, y: Integer | Float) -> Float`

Returns the angle in the plane between the positive x-axis and the ray from (0,0) to the point (x,y)

```lxm
Math.atan2(x, y)
```

### Parameters

- **`x`**: the x coordinate of the point.
- **`y`**: the y coordinate of the point.

### Errors

- **`BadArgumentError`**: when any of these conditions do not math.
  - the type of `x` is not an `Integer` or `Float`.
  - the type of `y` is not an `Integer` or `Float`.

### Examples

```lxm
Debug.log(Math.atan2(90, 15))     -- 1.4056476493802699
Debug.log(Math.atan2(15, 90))     -- 0.16514867741462683
```

## `.cbrt(number: Integer | Float) -> Float`

Returns the cube root of the specified number.

```lxm
Math.cbrt(number)
```

### Parameters

- **`number`**: the number to operate with.

### Errors

- **`BadArgumentError`**: when `number` is not an `Integer` or `Float`.

### Examples

```lxm
Debug.log(Math.cbrt(1))       -- 1.0
Debug.log(Math.cbrt(3))       -- 1.4422495703074083
Debug.log(Math.cbrt(9))       -- 2.080083823051904
```

## `.ceil(number: Integer | Float) -> Integer`

Returns the specified number rounded to the next integer.

```lxm
Math.ceil(number)
```

### Parameters

- **`number`**: the number to operate with.

### Errors

- **`BadArgumentError`**: when `number` is not an `Integer` or `Float`.

### Examples

```lxm
Debug.log(Math.ceil(1))       -- 1
Debug.log(Math.ceil(-3.4))    -- -3
```

## `.clz32(number: Integer) -> Integer`

Returns the number of leading zero bits in the 32-bit binary representation of the specified number.

```lxm
Math.clz32(number)
```

### Parameters

- **`number`**: the number to operate with.

### Errors

- **`BadArgumentError`**: when `number` is not an `Integer` or `Float`.

### Examples

```lxm
Debug.log(Math.clz32(1))      -- 31
Debug.log(Math.clz32(-3))     -- 0
```

## `.cos(number: Integer | Float) -> Float`

Returns the cosine of the specified number.

```lxm
Math.cos(number)
```

### Parameters

- **`number`**: the number to operate with. It must be in radians.

### Errors

- **`BadArgumentError`**: when `number` is not an `Integer` or `Float`.

### Examples

```lxm
Debug.log(Math.cos(0))       -- 1.0
Debug.log(Math.cos(0.5))     -- 0.8775825618903728
```

## `.cosh(number: Integer | Float) -> Float`

Returns the hyperbolic cosine of the specified number.

```lxm
Math.cosh(number)
```

### Parameters

- **`number`**: the number to operate with. It must be in radians.

### Errors

- **`BadArgumentError`**: when `number` is not an `Integer` or `Float`.

### Examples

```lxm
Debug.log(Math.cosh(1))      -- 1.5430806348152437
Debug.log(Math.cosh(1.5))    -- 2.352409615243247
```

## `.exp(number: Integer | Float) -> Float`

Returns the power of the Euler number to the specified number. 

```lxm
Math.exp(number)
```

### Parameters

- **`number`**: the number to operate with. It must be in radians.

### Errors

- **`BadArgumentError`**: when `number` is not an `Integer` or `Float`.

### Examples

```lxm
Debug.log(Math.exp(1))      -- 2.718281828459045
Debug.log(Math.exp(1.5))    -- 4.4816890703380645
```

## `.floor(number: Integer | Float) -> Integer`

Returns the specified number rounded to the previous integer.

```lxm
Math.floor(number)
```

### Parameters

- **`number`**: the number to operate with.

### Errors

- **`BadArgumentError`**: when `number` is not an `Integer` or `Float`.

### Examples

```lxm
Debug.log(Math.floor(1))       -- 1
Debug.log(Math.floor(-3.4))     -- -4
```

## `.hypot(...numbers: List<Integer | Float>) -> Float`

Returns the square root of the sum of squares of the specified numbers.

```lxm
Math.hypot(number1, ..., numberN)
```

### Parameters

- **`numbers`**: the numbers to operate with.

### Errors

- **`BadArgumentError`**: when any of the numbers are not an `Integer` or `Float`.

### Examples

```lxm
Debug.log(Math.hypot())               -- 0
Debug.log(Math.hypot(1, 3.4, -6))     -- 6.968500556073739
```

## `.ln(number: Integer | Float) -> Float`

Returns the natural logarithm of the specified number.

```lxm
Math.ln(number)
```

### Parameters

- **`number`**: the number to operate with. It must be in radians.

### Errors

- **`BadArgumentError`**: when `number` is not an `Integer` or `Float`.

### Examples

```lxm
Debug.log(Math.ln(Math.E))    -- 1
Debug.log(Math.ln(1.5))       -- 0.4054651081081644
Debug.log(Math.ln(1))         -- 0.0
```

## `.log10(number: Integer | Float) -> Float`

Returns the base 10 logarithm of the specified number.

```lxm
Math.log10(number)
```

### Parameters

- **`number`**: the number to operate with. It must be in radians.

### Errors

- **`BadArgumentError`**: when `number` is not an `Integer` or `Float`.

### Examples

```lxm
Debug.log(Math.log10(10))     -- 1
Debug.log(Math.log10(1.5))    -- 0.17609125905568124
Debug.log(Math.log10(1))      -- 0.0
```

## `.log2(number: Integer | Float) -> Float`

Returns the base 2 logarithm of the specified number.

```lxm
Math.log2(number)
```

### Parameters

- **`number`**: the number to operate with. It must be in radians.

### Errors

- **`BadArgumentError`**: when `number` is not an `Integer` or `Float`.

### Examples

```lxm
Debug.log(Math.log2(2))       -- 1
Debug.log(Math.log2(1.5))     -- 0.5849625007211562
Debug.log(Math.log2(1))       -- 0.0
```

## `.max(...numbers: List<Integer | Float>) -> Float`

Returns the maximum value of the specified ones.

```lxm
Math.max(number1, ..., numberN)
```

### Parameters

- **`numbers`**: the numbers to operate with.

### Errors

- **`BadArgumentError`**: when any of the numbers are not an `Integer` or `Float` or there is no number specified.

### Examples

```lxm
Debug.log(Math.max())             -- BadArgumentError
Debug.log(Math.max(1, 3.4, -6))   -- 3.4
```

## `.min(...numbers: List<Integer | Float>) -> Float`

Returns the minimum value of the specified ones.

```lxm
Math.min(number1, ..., numberN)
```

### Parameters

- **`numbers`**: the numbers to operate with.

### Errors

- **`BadArgumentError`**: when any of the numbers are not an `Integer` or `Float` or there is no number specified.

### Examples

```lxm
Debug.log(Math.min())             -- BadArgumentError
Debug.log(Math.min(1, 3.4, -6))   -- -6
```

## `.pow(base: Integer | Float, exponent: Integer | Float) -> Float | Nil`

Returns the `base` to the `exponent` power. The function returns `nil` if `base` is negative and `exponent` is fractional.

```lxm
Math.pow(base, exponent)
```

### Parameters

- **`base`**: the base.
- **`exponent`**: the exponent.

### Errors

- **`BadArgumentError`**: when any of these conditions do not math.
  - the type of `base` is not an `Integer` or `Float`.
  - the type of `exponent` is not an `Integer` or `Float`.

### Examples

```lxm
Debug.log(Math.pow(7, 3))     -- 342.0
Debug.log(Math.pow(4, 0.5))   -- 2.0
```

## `.random() -> Float`

Returns a random `Float` between 0 and 1.

```lxm
Math.random()
```

### Examples

```lxm
Debug.log(Math.random())      -- 0.8695149573936003
Debug.log(Math.random())      -- 0.4788946299878538
```

## `.round(number: Integer | Float) -> Integer`

Returns the specified number rounded to the nearest integer.

```lxm
Math.round(number)
```

### Parameters

- **`number`**: the number to operate with.

### Errors

- **`BadArgumentError`**: when `number` is not an `Integer` or `Float`.

### Examples

```lxm
Debug.log(Math.round(1))      -- 1
Debug.log(Math.round(-3.4))   -- -3
Debug.log(Math.round(2.7))    -- 3
```

## `.sign(number: Integer | Float) -> Integer`

Returns the sign of the specified number:

- 1 for positives.
- 0 for the zero.
- -1 for negatives.

```lxm
Math.sign(number)
```

### Parameters

- **`number`**: the number to operate with.

### Errors

- **`BadArgumentError`**: when `number` is not an `Integer` or `Float`.

### Examples

```lxm
Debug.log(Math.sign(-34))     -- -1
Debug.log(Math.sign(0))       -- 0
Debug.log(Math.sign(14.4))    -- 1
```

## `.sin(number: Integer | Float) -> Float`

Returns the sine of the specified number.

```lxm
Math.sin(number)
```

### Parameters

- **`number`**: the number to operate with. It must be in radians.

### Errors

- **`BadArgumentError`**: when `number` is not an `Integer` or `Float`.

### Examples

```lxm
Debug.log(Math.sin(0))       -- 0.0
Debug.log(Math.sin(0.5))     -- 0.479425538604203
```

## `.sinh(number: Integer | Float) -> Float`

Returns the hyperbolic sine of the specified number.

```lxm
Math.sinh(number)
```

### Parameters

- **`number`**: the number to operate with. It must be in radians.

### Errors

- **`BadArgumentError`**: when `number` is not an `Integer` or `Float`.

### Examples

```lxm
Debug.log(Math.sinh(1))      -- 1.1752011936438014
Debug.log(Math.sinh(1.5))    -- 2.1292794550948173
```

## `.sqrt(number: Integer | Float) -> Float | Nil`

Returns the square root of the specified number. If the number is negative, the function returns `nil`.

```lxm
Math.sqrt(number)
```

### Parameters

- **`number`**: the number to operate with.

### Errors

- **`BadArgumentError`**: when `number` is not an `Integer` or `Float`.

### Examples

```lxm
Debug.log(Math.sqrt(0))       -- 0.0
Debug.log(Math.sqrt(3))       -- 1.7320508075688772
Debug.log(Math.sqrt(9))       -- 3.0
Debug.log(Math.sqrt(-1))       -- nil
```

## `.tan(number: Integer | Float) -> Float`

Returns the tangent of the specified number.

```lxm
Math.tan(number)
```

### Parameters

- **`number`**: the number to operate with. It must be in radians.

### Errors

- **`BadArgumentError`**: when `number` is not an `Integer` or `Float`.

### Examples

```lxm
Debug.log(Math.tan(0))       -- 0.0
Debug.log(Math.tan(0.5))     -- 0.5463024898437905
```

## `.tanh(number: Integer | Float) -> Float`

Returns the hyperbolic tangent of the specified number.

```lxm
Math.tanh(number)
```

### Parameters

- **`number`**: the number to operate with. It must be in radians.

### Errors

- **`BadArgumentError`**: when `number` is not an `Integer` or `Float`.

### Examples

```lxm
Debug.log(Math.tanh(1))      -- 0.7615941559557649
Debug.log(Math.tanh(1.5))    -- 0.9051482536448664
```

## `.trunc(number: Integer | Float) -> Integer`

Returns the specified number without the decimal part.

```lxm
Math.trunc(number)
```

### Parameters

- **`number`**: the number to operate with.

### Errors

- **`BadArgumentError`**: when `number` is not an `Integer` or `Float`.

### Examples

```lxm
Debug.log(Math.trunc(1))      -- 1
Debug.log(Math.trunc(-3.4))   -- -3
```

# Properties

## `.E -> Float`

The Euler number.

```lxm
Math.E
```

## `.LN2 -> Float`

The natural logarithm of 2.

```lxm
Math.LN2
```

## `.LN10 -> Float`

The natural logarithm of 10.

```lxm
Math.LN10
```

## `.LOG10_E -> Float`

The base 10 logarithm of the Euler number.

```lxm
Math.LOG10_E
```

## `.LOG10_2 -> Float`

The base 10 logarithm of 2.

```lxm
Math.LOG10_2
```

## `.LOG2_E -> Float`

The base 2 logarithm of the Euler number.

```lxm
Math.LOG2_E
```

## `.LOG2_10 -> Float`

The base 2 logarithm of 10.

```lxm
Math.LOG2_10
```

## `.PI -> Float`

The PI number.

```lxm
Math.PI
```

## `.SQRT1_2 -> Float`

The square root of 0.5.

```lxm
Math.SQRT1_2
```

## `.SQRT2 -> Float`

The square root of 2.

```lxm
Math.SQRT2
```

## `.RAD2DEG -> Float`

The radian to degree proportion. It allows to change from radians to degrees with a multiplication.

```lxm
Math.RAD2DEG
```

## `.DEG2RAD -> Float`

The degree to radian proportion. It allows to change from degrees to radians with a multiplication.

```lxm
Math.DEG2RAD
```
