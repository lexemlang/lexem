
# Table of contents

- [Table of contents](#table-of-contents)
- [Methods](#methods)
  - [`.toString() -> String`](#tostring---string)
    - [Errors](#errors)
    - [Examples](#examples)
- [Operators](#operators)
  - [`.not() -> Logic`](#not---logic)
    - [Errors](#errors-1)
    - [Examples](#examples-1)
  - [`.logicAnd(right: Logic) -> Logic`](#logicandright-logic---logic)
    - [Parameters](#parameters)
    - [Errors](#errors-2)
    - [Examples](#examples-2)
  - [`.logicAnd(right: BitList) -> BitList`](#logicandright-bitlist---bitlist)
    - [Parameters](#parameters-1)
    - [Errors](#errors-3)
    - [Examples](#examples-3)
  - [`.logicOr(right: Logic) -> Logic`](#logicorright-logic---logic)
    - [Parameters](#parameters-2)
    - [Errors](#errors-4)
    - [Examples](#examples-4)
  - [`.logicOr(right: BitList) -> BitList`](#logicorright-bitlist---bitlist)
    - [Parameters](#parameters-3)
    - [Errors](#errors-5)
    - [Examples](#examples-5)
  - [`.logicXor(right: Logic) -> Logic`](#logicxorright-logic---logic)
    - [Parameters](#parameters-4)
    - [Errors](#errors-6)
    - [Examples](#examples-6)
  - [`.logicXor(right: BitList) -> BitList`](#logicxorright-bitlist---bitlist)
    - [Parameters](#parameters-5)
    - [Errors](#errors-7)
    - [Examples](#examples-7)

# Methods

## `.toString() -> String`

Returns a `String` representing the logic value.

```lxm
logic.toString()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Logic`.

### Examples

```lxm
let value = true

log(value.toString())   -- "true"
```

# Operators

## `.not() -> Logic`

Returns the logical negation of the `this` value, i.e `!this`.

```lxm
logic.not()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Logic`.

### Examples

```lxm
let value = false

log(value.not())    -- true
log(!value)         -- true Implicit calling
```

## `.logicAnd(right: Logic) -> Logic`

Returns the result of applying the *and* operator between the `this` and `right` values, i.e `this & right`.

```lxm
logic.logicAnd(right)
```

### Parameters

- **`right`**: the right operand.

### Errors

- **`BadArgumentError`**: when the type of `right` is incorrect.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Logic`.

### Examples

```lxm
let left = false
let right = true

log(left.logicAnd(right))   -- false
log(left.logicAnd(nil))     -- BadArgumentError
log(left & right)           -- false Implicit calling
```

## `.logicAnd(right: BitList) -> BitList`

Returns the result of applying the *and* operator between every bit of `right` and the `this` value, i.e `this & right`.

```lxm
bitlist.logicAnd(right)
```

### Parameters

- **`right`**: the right operand.

### Errors

- **`BadArgumentError`**: when the type of `right` is incorrect.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `BitList`.

### Examples

```lxm
let left = true
let right = 0b"1001"

log(left.logicAnd(right))   -- 0b"1001"
log(left.logicAnd(nil))     -- BadArgumentError
log(left & right)           -- 0b"1001" Implicit calling
```

## `.logicOr(right: Logic) -> Logic`

Returns the result of applying the *or* operator between the `this` and `right` values, i.e `this | right`.

```lxm
logic.logicOr(right)
```

### Parameters

- **`right`**: the right operand.

### Errors

- **`BadArgumentError`**: when the type of `right` is incorrect.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Logic`.

### Examples

```lxm
let left = false
let right = true

log(left.logicOr(right))    -- true
log(left.logicOr(nil))      -- BadArgumentError
log(left | right)           -- true Implicit calling
```

## `.logicOr(right: BitList) -> BitList`

Returns the result of applying the *or* operator between every bit of `right` and the `this` value, i.e `this | right`.

```lxm
bitlist.logicOr(right)
```

### Parameters

- **`right`**: the right operand.

### Errors

- **`BadArgumentError`**: when the type of `right` is incorrect.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `BitList`.

### Examples

```lxm
let left = true
let right = 0b"1001"

log(left.logicOr(right))    -- 0b"1111"
log(left.logicOr(nil))      -- BadArgumentError
log(left | right)           -- 0b"1111" Implicit calling
```

## `.logicXor(right: Logic) -> Logic`

Returns the result of applying the *xor* operator between the `this` and `right` values, i.e `this ^ right`.

```lxm
logic.logicXor(right)
```

### Parameters

- **`right`**: the right operand.

### Errors

- **`BadArgumentError`**: when the type of `right` is incorrect.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Logic`.

### Examples

```lxm
let left = false
let right = true

log(left.logicXor(right))   -- true
log(left.logicXor(nil))     -- BadArgumentError
log(left ^ right)           -- true Implicit calling
```

## `.logicXor(right: BitList) -> BitList`

Returns the result of applying the *xor* operator between every bit of `right` and the `this` value, i.e `this ^ right`.

```lxm
bitlist.logicXor(right)
```

### Parameters

- **`right`**: the right operand.

### Errors

- **`BadArgumentError`**: when the type of `right` is incorrect.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `BitList`.

### Examples

```lxm
let left = true
let right = 0b"1001"

log(left.logicXor(right))   -- 0b"0110"
log(left.logicXor(nil))     -- BadArgumentError
log(left ^ right)           -- 0b"0110" Implicit calling
```
