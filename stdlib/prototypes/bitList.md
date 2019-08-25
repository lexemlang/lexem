
# Table of contents

- [Table of contents](#table-of-contents)
- [Methods](#methods)
  - [`.toString(radix: Integer) -> value: String`](#tostringradix-integer---value-string)
  - [`.toString() -> String`](#tostring---string)
- [Operators](#operators)
  - [`.not() -> BitList`](#not---bitlist)
  - [`.logicAnd(right: Logic) -> BitList`](#logicandright-logic---bitlist)
  - [`.logicAnd(right: BitList) -> BitList`](#logicandright-bitlist---bitlist)
  - [`.logicOr(right: Logic) -> BitList`](#logicorright-logic---bitlist)
  - [`.logicOr(right: BitList) -> BitList`](#logicorright-bitlist---bitlist)
  - [`.logicXor(right: Logic) -> BitList`](#logicxorright-logic---bitlist)
  - [`.logicXor(right: BitList) -> BitList`](#logicxorright-bitlist---bitlist)

# Methods

## `.toString(radix: Integer) -> value: String`

Returns the `String` representation of the binary list value in the specified radix `radix`.

```lxm
bitlist.toRadix(radix)
```

### Parameters

- **`radix`**: the radix of the resulting number. Only valid: 2, 8 or 16.

### Errors

- **`BadArgumentError`**: when `radix` is not one of 2, 8 or 16.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `BitList`.

### Examples

```lxm
let value = 0b"1000"

log(value.toString(2))      -- "0b\"1000\""
log(value.toString(8))      -- "0o\"40\""
log(value.toString(16))     -- "0x\"8\""
```

## `.toString() -> String`

Returns a `String` representing the binary list value.

```lxm
bitlist.toString()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `BitList`.

### Examples

```lxm
let valueBin = 0b"01"
let valueOct = 0o"36"
let valueHex = 0x"F2"

log(valueBin.toString())   -- "0b\"01\""
log(valueOct.toString())   -- "0o\"36\""
log(valueHex.toString())   -- "0x\"F2\""
```

# Operators

## `.not() -> BitList`

Returns the logical negation of the `this` value negating all of its internal bits, i.e `!this`.

```lxm
bitlist.not()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `BitList`.

### Examples

```lxm
let value = 0b"1001"

log(value.not())    -- 0b"0110"
log(!value)         -- 0b"0110" Implicit calling
```

## `.logicAnd(right: Logic) -> BitList`

Returns the result of applying the *and* operator between every bit of `this` and the `right` value, i.e `this & right`.

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
let left = 0b"1001"
let right = true

log(left.logicAnd(right))   -- 0b"1001"
log(left.logicAnd(nil))     -- BadArgumentError
log(left & right)           -- 0b"1001" Implicit calling
```

## `.logicAnd(right: BitList) -> BitList`

Returns the result of applying the *and* operator between every bit of the `this` and `right` values, i.e `this & right`.

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
let left =  0b"1001"
let right = 0b"110011"

log(left.logicAnd(right))   -- 0b"100000"
log(left.logicAnd(nil))     -- BadArgumentError
log(left & right)           -- 0b"100000" Implicit calling
```

## `.logicOr(right: Logic) -> BitList`

Returns the result of applying the *or* operator between every bit of `this` and the `right` value, i.e `this | right`.

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
let left = 0b"1001"
let right = true

log(left.logicOr(right))    -- 0b"1111"
log(left.logicOr(nil))      -- BadArgumentError
log(left | right)           -- 0b"1111" Implicit calling
```

## `.logicOr(right: BitList) -> BitList`

Returns the result of applying the *or* operator between every bit of the `this` and `right` values, i.e `this | right`.

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
let left =  0b"1001"
let right = 0b"110011"

log(left.logicOr(right))    -- 0b"110111"
log(left.logicOr(nil))      -- BadArgumentError
log(left | right)           -- 0b"110111" Implicit calling
```

## `.logicXor(right: Logic) -> BitList`

Returns the result of applying the *xor* operator between every bit of `this` and the `right` value, i.e `this ^ right`.

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
let left = 0b"1001"
let right = true

log(left.logicXor(right))   -- 0b"0110"
log(left.logicXor(nil))     -- BadArgumentError
log(left ^ right)           -- 0b"0110" Implicit calling
```

## `.logicXor(right: BitList) -> BitList`

Returns the result of applying the *xor* operator between every bit of the `this` and `right` values, i.e `this ^ right`.

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
let left = 0b"1001"
let right = 0b"110011"

log(left.logicXor(right))   -- 0b"010111"
log(left.logicXor(nil))     -- BadArgumentError
log(left ^ right)           -- 0b"010111" Implicit calling
```
