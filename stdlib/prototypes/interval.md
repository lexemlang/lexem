
# Table of contents

- [Table of contents](#table-of-contents)
- [Methods](#methods)
  - [.toString() -&gt; String](#tostring--gt-string)
  - [.isEmpty() -&gt; Logic](#isempty--gt-logic)
  - [.pointCount() -&gt; Integer](#pointcount--gt-integer)
  - [.unicodeNot() -&gt; Logic](#unicodenot--gt-logic)
- [Operators](#operators)
  - [.not() -&gt; Logic](#not--gt-logic)
  - [.add(right: Integer | Interval) -&gt; Interval](#addright-integer--interval--gt-interval)
  - [.sub(right: Integer | Interval) -&gt; Interval](#subright-integer--interval--gt-interval)
  - [.logicAnd(right: Integer | Interval) -&gt; Interval](#logicandright-integer--interval--gt-interval)
  - [.logicOr(right: Integer | Interval) -&gt; Interval](#logicorright-integer--interval--gt-interval)
  - [.logicXor(right: Integer | Interval) -&gt; Interval](#logicxorright-integer--interval--gt-interval)

# Methods

## `.toString() -> String`

Returns a `String` representing the interval value.

```lxm
interval.toString()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not an `Interval`.

### Examples

```lxm
let value = itv![2 3 10]

Debug.log(value.toString()) -- [2..3] U [10]
```

## `.isEmpty() -> Logic`

Returns whether the interval is empty or not.

```lxm
interval.isEmpty()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not an `Interval`.

### Examples

```lxm
let value = itv![2 3 10]

Debug.log(value.isEmpty())  -- false
```

## `.pointCount() -> Integer`

Returns the number of points of the interval.

```lxm
interval.pointCount()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not an `Interval`.

### Examples

```lxm
let value = itv![2 3 10]

Debug.log(value.pointCount())   -- 3
```

## `.unicodeNot() -> Logic`

Returns the logical negation of the `this` value, i.e `!this`, inside the bounds of the valid Unicode points.

```lxm
interval.not()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not an `Interval`.

### Examples

```lxm
let value = itv![2 3 10]

Debug.log(value.unicodeNot())   -- [0, 1] U [4, 9] U [11, 1114111]
```

# Operators

## `.not() -> Logic`

Returns the logical negation of the `this` value, i.e `!this`.

```lxm
interval.not()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not an `Interval`.

### Examples

```lxm
let value = itv![2 3 10]

Debug.log(value.not())    -- [0, 1] U [4, 9] U [11, 2147483647]
Debug.log(!value)         -- [0, 1] U [4, 9] U [11, 2147483647] Implicit calling
```

## `.add(right: Integer | Interval) -> Interval`

Returns the addition of the `this` value to the `right` value, i.e `this + right`.

```lxm
interval.add(right)
```

### Parameters

- **`right`**: the right operand.

### Errors

- **`BadArgumentError`**: when the type of `right` is incorrect.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not an `Interval`.

### Examples

```lxm
let left = itv![2 3 10]
let rightInt = 4
let rightInterval = itv![7..29]

Debug.log(left.add(rightInt))       -- [2..4] U [10]
Debug.log(left.add(rightInterval))  -- [2..3] U [7..29]
Debug.log(left.add(nil))            -- BadArgumentError
Debug.log(left + rightInt)          -- [2..4] U [10] Implicit calling
```

## `.sub(right: Integer | Interval) -> Interval`

Returns the subtraction of the `right` value from the `this` value, i.e `this - right`.

```lxm
interval.add(right)
```

### Parameters

- **`right`**: the right operand.

### Errors

- **`BadArgumentError`**: when the type of `right` is incorrect.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not an `Interval`.

### Examples

```lxm
let left = itv![2 3 10]
let rightInt = 2
let rightInterval = itv![7..29]

Debug.log(left.sub(rightInt))       -- [3] U [10]
Debug.log(left.sub(rightInterval))  -- [2..3]
Debug.log(left.sub(nil))            -- BadArgumentError
Debug.log(left - rightInt)          -- [3] U [10] Implicit calling
```

## `.logicAnd(right: Integer | Interval) -> Interval`

Returns the result of applying the *and* operator between every bit of `right` and the `this` value, i.e `this & right`.

```lxm
interval.logicAnd(right)
```

### Parameters

- **`right`**: the right operand.

### Errors

- **`BadArgumentError`**: when the type of `right` is incorrect.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not an `Interval`.

### Examples

```lxm
let left = itv![2 3 10]
let rightInt = 2
let rightInterval = itv![7..29]

Debug.log(left.logicAnd(rightInt))      -- [2]
Debug.log(left.logicAnd(rightInterval)) -- [10]
Debug.log(left.logicAnd(nil))           -- BadArgumentError
Debug.log(left & rightInt)              -- [2] Implicit calling
```

## `.logicOr(right: Integer | Interval) -> Interval`

Returns the result of applying the *or* operator between every bit of `right` and the `this` value, i.e `this | right`.

```lxm
interval.logicOr(right)
```

### Parameters

- **`right`**: the right operand.

### Errors

- **`BadArgumentError`**: when the type of `right` is incorrect.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not an `Interval`.

### Examples

```lxm
let left = itv![2 3 10]
let rightInt = 4
let rightInterval = itv![7..29]

Debug.log(left.logicOr(rightInt))       -- [2..4] U [10]
Debug.log(left.logicOr(rightInterval))  -- [2..3] U [7..29]
Debug.log(left.logicOr(nil))            -- BadArgumentError
Debug.log(left | rightInt)              -- [2..4] U [10] Implicit calling
```

## `.logicXor(right: Integer | Interval) -> Interval`

Returns the result of applying the *xor* operator between the `this` and `right` values, i.e `this ^ right`.

```lxm
interval.logicXor(right)
```

### Parameters

- **`right`**: the right operand.

### Errors

- **`BadArgumentError`**: when the type of `right` is incorrect.
- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not an `Interval`.

### Examples

```lxm
let left = itv![2 3 10]
let rightInt = 2
let rightInterval = itv![7..29]

Debug.log(left.logicXor(rightInt))      -- [3] U [10]
Debug.log(left.logicXor(rightInterval)) -- [2..3] U [7..9] U [11..29]
Debug.log(left.logicXor(nil))           -- BadArgumentError
Debug.log(left ^ rightInt)              -- [3] U [10] Implicit calling
```
