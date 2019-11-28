
# Table of contents

- [Table of contents](#table-of-contents)
- [Methods](#methods)
  - [`.toString() -> String`](#tostring---string)
- [Operators](#operators)
  - [`.not() -> Logic`](#not---logic)
  - [`.logicAnd(right: Logic) -> Logic`](#logicandright-logic---logic)
  - [`.logicAnd(right: BitList) -> BitList`](#logicandright-bitlist---bitlist)
  - [`.logicOr(right: Logic) -> Logic`](#logicorright-logic---logic)
  - [`.logicOr(right: BitList) -> BitList`](#logicorright-bitlist---bitlist)
  - [`.logicXor(right: Logic) -> Logic`](#logicxorright-logic---logic)
  - [`.logicXor(right: BitList) -> BitList`](#logicxorright-bitlist---bitlist)

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

Debug.log(value.toString())   -- "true"
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

Debug.log(value.not())    -- true
Debug.log(!value)         -- false Implicit calling
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

Debug.log(left.logicAnd(right))   -- false
Debug.log(left.logicAnd(nil))     -- BadArgumentError
Debug.log(left & right)           -- false Implicit calling
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

Debug.log(left.logicAnd(right))   -- 0b"1001"
Debug.log(left.logicAnd(nil))     -- BadArgumentError
Debug.log(left & right)           -- 0b"1001" Implicit calling
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

Debug.log(left.logicOr(right))    -- true
Debug.log(left.logicOr(nil))      -- BadArgumentError
Debug.log(left | right)           -- true Implicit calling
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

Debug.log(left.logicOr(right))    -- 0b"1111"
Debug.log(left.logicOr(nil))      -- BadArgumentError
Debug.log(left | right)           -- 0b"1111" Implicit calling
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

Debug.log(left.logicXor(right))   -- true
Debug.log(left.logicXor(nil))     -- BadArgumentError
Debug.log(left ^ right)           -- true Implicit calling
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

Debug.log(left.logicXor(right))   -- 0b"0110"
Debug.log(left.logicXor(nil))     -- BadArgumentError
Debug.log(left ^ right)           -- 0b"0110" Implicit calling
```
