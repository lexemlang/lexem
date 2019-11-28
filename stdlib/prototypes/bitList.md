
# Table of contents

- [Table of contents](#table-of-contents)
- [Methods](#methods)
  - [`.toString(radix: Integer) -> value: String`](#tostringradix-integer---value-string)
  - [`.toString() -> String`](#tostring---string)
- [Operators](#operators)
  - [`.bitwiseNegation() -> BitList`](#bitwisenegation---bitlist)
  - [`.logicAnd(right: Logic) -> BitList`](#logicandright-logic---bitlist)
  - [`.logicAnd(right: BitList) -> BitList`](#logicandright-bitlist---bitlist)
  - [`.logicOr(right: Logic) -> BitList`](#logicorright-logic---bitlist)
  - [`.logicOr(right: BitList) -> BitList`](#logicorright-bitlist---bitlist)
  - [`.logicXor(right: Logic) -> BitList`](#logicxorright-logic---bitlist)
  - [`.logicXor(right: BitList) -> BitList`](#logicxorright-bitlist---bitlist)
  - [`.leftShift(right: Integer) -> BitList`](#leftshiftright-integer---bitlist)
  - [`.rightShift(right: Integer) -> BitList`](#rightshiftright-integer---bitlist)
  - [`.leftRotate(right: Integer) -> BitList`](#leftrotateright-integer---bitlist)
  - [`.rightRotate(right: Integer) -> BitList`](#rightrotateright-integer---bitlist)
- [Accesses](#accesses)
  - [`[index: Integer] -> Logic`](#index-integer---logic)

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

Debug.log(value.toString(2))      -- "0b\"1000\""
Debug.log(value.toString(8))      -- "0o\"40\""
Debug.log(value.toString(16))     -- "0x\"8\""
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

Debug.log(valueBin.toString())   -- "0b\"01\""
Debug.log(valueOct.toString())   -- "0o\"36\""
Debug.log(valueHex.toString())   -- "0x\"F2\""
```

# Operators

## `.bitwiseNegation() -> BitList`

Returns the logical negation of the `this` value negating all of its internal bits, i.e `!this`.

```lxm
bitlist.bitwiseNegation()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `BitList`.

### Examples

```lxm
let value = 0b"1001"

Debug.log(value.bitwiseNegation())    -- 0b"0110"
Debug.log(~value)                     -- 0b"0110" Implicit calling
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

Debug.log(left.logicAnd(right))   -- 0b"1001"
Debug.log(left.logicAnd(nil))     -- BadArgumentError
Debug.log(left & right)           -- 0b"1001" Implicit calling
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

Debug.log(left.logicAnd(right))   -- 0b"100000"
Debug.log(left.logicAnd(nil))     -- BadArgumentError
Debug.log(left & right)           -- 0b"100000" Implicit calling
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

Debug.log(left.logicOr(right))    -- 0b"1111"
Debug.log(left.logicOr(nil))      -- BadArgumentError
Debug.log(left | right)           -- 0b"1111" Implicit calling
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

Debug.log(left.logicOr(right))    -- 0b"110111"
Debug.log(left.logicOr(nil))      -- BadArgumentError
Debug.log(left | right)           -- 0b"110111" Implicit calling
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

Debug.log(left.logicXor(right))   -- 0b"0110"
Debug.log(left.logicXor(nil))     -- BadArgumentError
Debug.log(left ^ right)           -- 0b"0110" Implicit calling
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

Debug.log(left.logicXor(right))   -- 0b"010111"
Debug.log(left.logicXor(nil))     -- BadArgumentError
Debug.log(left ^ right)           -- 0b"010111" Implicit calling
```

## `.leftShift(right: Integer) -> BitList`

Returns the current bitlist with all its bits moved `right` bits to the left applying 0s at the end.

```lxm
bitlist.leftShift(right)
```

### Parameters

- **`right`**: the right operand.

### Errors

- **`BadArgumentError`**: when the type of `right` is not a positive `Integer`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `BitList`.

### Examples

```lxm
let left = 0b"1001"

Debug.log(left.leftShift(2))      -- 0b"100100"
Debug.log(left.leftShift(nil))    -- BadArgumentError
Debug.log(left << 2)              -- 0b"100100" Implicit calling
```

## `.rightShift(right: Integer) -> BitList`

Returns the current bitlist with all its bits moved `right` bits to the right, removing those bits that do not fit inside anymore.

```lxm
bitlist.rightShift(right)
```

### Parameters

- **`right`**: the right operand.

### Errors

- **`BadArgumentError`**: when the type of `right` is not a positive `Integer`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `BitList`.

### Examples

```lxm
let left = 0b"1001"

Debug.log(left.rightShift(2))     -- 0b"10"
Debug.log(left.rightShift(nil))   -- BadArgumentError
Debug.log(left >> 2)              -- 0b"10" Implicit calling
```

## `.leftRotate(right: Integer) -> BitList`

Returns the current bitlist rotated `right` bits to the left.

```lxm
bitlist.leftRotate(right)
```

### Parameters

- **`right`**: the right operand.

### Errors

- **`BadArgumentError`**: when the type of `right` is not a positive `Integer`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `BitList`.

### Examples

```lxm
let left = 0b"111000"

Debug.log(left.leftRotate(2))     -- 0b"100011"
Debug.log(left.leftRotate(nil))   -- BadArgumentError
Debug.log(left << 2)              -- 0b"100011" Implicit calling
```

## `.rightRotate(right: Integer) -> BitList`

Returns the current bitlist rotated `right` bits to the right.

```lxm
bitlist.rightRotate(right)
```

### Parameters

- **`right`**: the right operand.

### Errors

- **`BadArgumentError`**: when the type of `right` is not a positive `Integer`.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `BitList`.

### Examples

```lxm
let left = 0b"111000"

Debug.log(left.rightRotate(2))    -- 0b"001110"
Debug.log(left.rightRotate(nil))  -- BadArgumentError
Debug.log(left >> 2)              -- 0b"001110" Implicit calling
```

# Accesses

## `[index: Integer] -> Logic`

Returns the bit at the specified position.

```lxm
bitlist[index]
```

### Parameters

- **`index`**: the position of the bit.

### Errors

- **`BadArgumentError`**: when the type of `index` is not an `Integer`.
- **`IndexOutOfBounds`**: when the `index` is greater than the last valid index.  
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `String`.

### Examples

```lxm
let bitlist = 0b"1100"

Debug.log(bitlist[nil])   -- BadArgumentError
Debug.log(bitlist[0])     -- true
Debug.log(bitlist[1])     -- true
Debug.log(bitlist[2])     -- false
Debug.log(bitlist[3])     -- false
```
