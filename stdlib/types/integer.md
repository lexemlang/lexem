
# Table of contents

- [Table of contents](#table-of-contents)
- [Methods](#methods)
  - [.parse(value: String) -&gt; Integer | Nil](#parsevalue-string--gt-integer--nil)
  - [.parse(value: String, radix: Integer) -&gt; Integer | Nil](#parsevalue-string-radix-integer--gt-integer--nil)
- [Properties](#properties)
  - [.prototype -&gt; Object](#prototype--gt-object)
  - [.MaxValue -&gt; Object](#maxvalue--gt-object)
  - [.MinValue -&gt; Object](#minvalue--gt-object)

# Methods

## `.parse(value: String) -> Integer | Nil`

Returns an `Integer` value equivalent to the specified string representation. This method searches for one of the available number prefixes (`"0b"`, `"0o"`, `"0d"` and `"0x"`) to get the radix of the number or defaults to 10 if it is not present. The function returns `nil` if it can not parse the `value`.

```lxm
Integer.parse(value)
```

### Parameters

- **`value`**: the string representation of the number.

### Errors

- **`BadArgumentError`**: when `value` is not a `String`.

### Examples

```lxm
Debug.log(Integer.parse("0b10101"))   -- 21
Debug.log(Integer.parse("0o25"))      -- 21
Debug.log(Integer.parse("0d21"))      -- 21
Debug.log(Integer.parse("0x15"))      -- 21
Debug.log(Integer.parse("21"))        -- 21
Debug.log(Integer.parse(nil))         -- BadArgumentError
```

## `.parse(value: String, radix: Integer) -> Integer | Nil`

Returns an `Integer` value equivalent to the specified string representation written in the specified radix. The function returns `nil` if it can not parse the `value`.

```lxm
Integer.parse(value, radix)
```

### Parameters

- **`value`**: the string representation of the number.
- **`radix`**: the radix in which the number is represented in the string.

### Errors

- **`BadArgumentError`**: when any of these conditions do not math.
  - the type of `value` is not a `String`.
  - `radix` is not one of 2, 8, 10 or 16.

### Examples

```lxm
Debug.log(Integer.parse("10101", 2))  -- 21
Debug.log(Integer.parse("25", 8))     -- 21
Debug.log(Integer.parse("21", 10))    -- 21
Debug.log(Integer.parse("15", 16))    -- 21
Debug.log(Integer.parse(nil))         -- BadArgumentError
```

# Properties

## `.prototype -> Object`

The prototype of the type.

```lxm
Integer.prototype
```

## `.MaxValue -> Object`

The maximum integer value.

```lxm
Integer.MaxValue
```

## `.MinValue -> Object`

The minimum integer value.

```lxm
Integer.MinValue
```
