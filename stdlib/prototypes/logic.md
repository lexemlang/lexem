
# Table of contents

- [Table of contents](#table-of-contents)
- [Methods](#methods)
  - [.toString() -&gt; String](#tostring--gt-string)
- [Operators](#operators)
  - [.not() -&gt; Logic](#not--gt-logic)
  - [.logicAnd(right: Logic) -&gt; Logic](#logicandright-logic--gt-logic)
  - [.logicOr(right: Logic) -&gt; Logic](#logicorright-logic--gt-logic)
  - [.logicXor(right: Logic) -&gt; Logic](#logicxorright-logic--gt-logic)

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
Debug.log(!value)         -- true Implicit calling
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
