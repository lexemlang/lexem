
# Index

- [Index](#Index)
- [Types, prototypes and literals](#Types-prototypes-and-literals)
  - [Null type](#Null-type)
  - [Logic type](#Logic-type)
  - [Integer type](#Integer-type)
  - [Float type](#Float-type)
  - [String type](#String-type)
    - [Escapes](#Escapes)
    - [Dynamic escape](#Dynamic-escape)
  - [Interval type](#Interval-type)
    - [Internal rules](#Internal-rules)
    - [Escapes](#Escapes-1)
    - [Dynamic escape](#Dynamic-escape-1)
      - [Sub-intervals](#Sub-intervals)
  - [BitList type](#BitList-type)
    - [Dynamic escape](#Dynamic-escape-2)
  - [List type](#List-type)
  - [Set type](#Set-type)
  - [Object type](#Object-type)
    - [Complex property names](#Complex-property-names)
    - [Constant properties](#Constant-properties)
    - [Simplifications (syntactic sugar)](#Simplifications-syntactic-sugar)
    - [Property-style object definition](#Property-style-object-definition)
  - [Map types](#Map-types)
  - [Function type](#Function-type)
  - [Expression type](#Expression-type)

# Types, prototypes and literals

In Lexem everything is an object even the primitives but they are immutable to behave like in any other language.

Every type has three elements:

- Type: an object that represents the type and has extra functionality or information for that type. All types are set in the global context so they can be accessed directly or using `global.Type`.
- Prototype: an object that contains all the internal functionality that all instances will inherit. It can be accessed through `Type.prototype` or using `Object.getPrototype(<value>)`.
- Literal: a textual representation of a type's value.

All objects have a prototype and inherit directly or indirectly from the `Object` prototype, creating a hierarchy of inherited functionality.

## Null type

Represents undefined values and error or void states. It has only just one possible value.

- Type: `Null`
- Prototype: `Null.prototype`
- Literals:

  | Literal | Meaning |
  |:-------:|:--------|
  |`null`|The unique possible value of the type.|

> **Note**: it is interpreted as false when a truthiness check is required.

## Logic type

Represents logical states, like truth and falsity.

- Type: `Logic`
- Prototype: `Logic.prototype`
- Literals:

  | Literal | Meaning |
  |:-------:|:--------|
  |`false`|False logic value.|
  |`true`|True logic value.|

## Integer type

Represents integer numbers.

- Type: `Integer`
- Prototype: `Integer.prototype`
- Literals:

  | Literal | Meaning |
  |:-------:|:--------|
  |`0b01`|Integer number represented in binary base.|
  |`0o01234567`|Integer number represented in octal base.|
  |`0d0123456789`|Integer number represented in decimal base. The `0d` prefix is optional.|
  |`0x0123456789abcdefABCDEF`|Integer number represented in hexadecimal base.|

> **Note**: numbers can be divided with one `_`, any number of times, so `0b10_1110011_11` and `213_12_58_7` are correct but `0x_342_abd`, `0o23_227_` and `123___443` are incorrect.

## Float type

Represents real numbers.

- Type: `Float`
- Prototype: `Float.prototype`
- Literals:

  | Literal | Meaning |
  |:-------:|:--------|
  |`0b01.01e-01`|Real number represented in binary base. The exponent symbol can be either `e` or `p`.|
  |`0o01.23e-45`|Real number represented in octal base. The exponent symbol can be either `e` or `p`.|
  |`0d01.26e-48`|Real number represented in decimal base. The `0d` prefix is optional. The exponent symbol can be either `e` or `p`.|
  |`0x0c.23p-F5`|Real number represented in hexadecimal base. The exponent symbol can be only `p`.|

> **Note**: each integer part of the literal can be divided with `_` following the rules of the `Integer` type.

## String type

Represents textual data.

- Type: `String`
- Prototype: `String.prototype`
- Literals:

  | Literal | Meaning |
  |:-------:|:--------|
  |`$"text with " inside"$`|Char string that accepts escapes. The `$` are optional and are used to embed any type of content, so it can be used any number of them.|
  |`lit!$"text with " inside"$`|Char string that does not accept escapes. You can use any number of `$` (or none at all) to embed any type of content avoiding annoying escapes.|

### Escapes

Escapes are used to represent characters that don't have a visual representation. All escapes start with a `\` followed by an visual character:

| Escape | Meaning |
|:------:|:--------|
| `\u{<num>}` | Specifies an Unicode point using an integer literal. Default is hexadecimal so its prefix is optional but decimal numbers require it. |
| `\uHHHHHH` | Specifies an Unicode point using six hexadecimal characters. |
| `\p{<num>}` | Specifies a 32-bit point using an integer literal. Default is hexadecimal so its prefix is optional but decimal numbers require it. |
| `\pHHHHHHHH` | Specifies a 32-bit point using eight hexadecimal characters. |
| `\t` | Horizontal Tab (`HT`): Unicode(`00000009`) |
| `\n` | Line Feed(`LF`): Unicode(`0000000A`) |
| `\r` | Carriage Return (`CR`): Unicode(`0000000D`) |

> **Note**: if any other character is escaped, it is interpreted as a no-escape e.g. `\a = a`.

### Dynamic escape

Dynamic escapes allow to include the result of an expression in the middle of the literal, converting it to its textual representation (in fact calling its `toString` function) and joining it with the rest of the string.

The patten is `"...\( expression )..."`:

```lexem
var num = 3
var str = "buy \(num) things"
#- str == "buy 3 things"
```

## Interval type

Represents serialized binary data.

- Type: `Interval`
- Prototype: `Interval.prototype`
- Literals:
  | Literal | Meaning |
  |:-------:|:--------|
  |`itv![1..0b1010 50 54..69]`|Complex interval of integer values.|
  |`uitv![a..z [- d]]`|Complex interval of Unicode point values.|

> **Note**: the whitespaces are only used to improve the readability, therefore they are ignored.

### Internal rules

Intervals have the ability to create complex structures with the following rules:

| Rules | Syntax | Meaning |
|:-----:|:------:|:--------|
| Negation | `!` | This operator at the beginning of the interval makes the resulting interval will be exclusive, i.e. the resulting interval will contain the negation of the defined one. |
| Point | `x` | Adds the value to the interval. Whitespaces are ignored and must be escaped. |
| Range | `x..y` | Adds the range of values to the interval. |
| Escape | `\x` | Same as a point but using an escape instead. |
| Sub-interval | | _See sub-intervals section_ |

### Escapes

Interval's escapes are the same of String's escapes plus:

| Escape | Meaning |
|:------:|:--------|
| `\ ` | Space: Unicode(`00000020`) |

### Dynamic escape

Dynamic escapes allow to include the result of an expression in the middle of the interval, getting the value and elaborating complex dynamic intervals.

The patten is `[...\( expression )...]` and can be used also as one of the bounds of a range, for example:

```lexem
var x = "b"
var y = "p"
var itv = [a\(x) \(num)..t]
#- itv == [ab p..t]
```

#### Sub-intervals

Intervals are complex sets of values inside a full range `[0, FFFFFFFF]`. Due to that, intervals are able to perform set operations with them using sub-intervals.

The *sub-interval patten* `[... [op body] ...]` contains an operator, which defines how to join the sub-interval with its parent, and a body to define its content. The body accepts the same rules of the main one, even another sub-intervals.

| Operator | Syntax | Meaning |
|:--------:|:------:|:--------|
| Addition | `+` | Combines the intervals picking all the elements from both. The operator can be omitted only if the reversion operator is not included. |
| Subtraction | `-` | Combines the intervals removing the current interval's elements from the parent interval. |
| Common section | `&` | Combines the intervals returning only those elements that appear in both intervals. |
| Not common section | `^` | Combines the intervals returning those elements that appear just only in one of both intervals. |
| Reversion | `op!` | Reverts the interval and then performs the operation indicated by `op`. |

## BitList type

Represents serialized binary data.

- Type: `BitList`
- Prototype: `BitList.prototype`
- Literals:

  | Literal | Meaning |
  |:-------:|:--------|
  |`0b"1010 0101"`|Data sequence encoded as a binary list.|
  |`0o"345 123"`|Data sequence encoded as an octal sequence.|
  |`0x"A3 B5 12"`|Data sequence encoded as an hexadecimal sequence.|

> **Note**: the whitespaces are only used to improve the readability therefore they are ignored.

### Dynamic escape

Dynamic escapes allow to include the result of an expression in the middle of the literal. The result should be of type `BitList` or `Integer` to join it to the rest of the binary sequence.

The patten is `0b"...\( expression )..."` and for example:

```lexem
var num = 6
var res = 0b"0101 \(num) 0111"
#- res == 0b"0101 0110 0111"
```

## List type

Represents an ordered sequence of elements. They can be indexed starting from 0.

- Type: `List`
- Prototype: `List.prototype`
- Literals:

  | Literal | Meaning |
  |:-------:|:--------|
  |`[]`|An empty list.|
  |`[value0, value1]`|A list of elements.|
  |`#[value0, value1]`|A constant list of elements. They can't be changed and the list can't be extended or shrunk.|

> **Note**: values could be complex expressions and of any type.

## Set type

Represents a no-ordered group of elements. They can't be indexed.

- Type: `Set`
- Prototype: `Set.prototype`
- Literals:

  | Literal | Meaning |
  |:-------:|:--------|
  |`set![]`|An empty set.|
  |`set![value0, value1]`|A set of elements.|
  |`set!#[value0, value1]`|A constant set of elements. They can't be changed and the set can't be extended or shrunk.|

> **Note**: values could be complex expressions and of any type.

## Object type

Represents a no-ordered group of elements, each one with a name (`String`) that represents it.

- Type: `Object`
- Prototype: `Object.prototype`. it is the root prototype of every value in its prototype chain.
- Literals:

  | Literal | Meaning |
  |:-------:|:--------|
  |`{}`|An empty object.|
  |`{name0: value0, name1: value1}`|An object filled with elements, each one with a name.|
  |`#{name0: value0, name1: value1}`|An object filled with elements, each one with a name. They can't be changed and the object can't be extended or shrunk. |

> **Note**: values could be complex expressions and of any type.

### Complex property names

Names can be freely changed by any literal string or a escaped expression to create computed names. For example, all of the following examples are equivalent:

```lexem
{name: 3}
{"name": 3}
{$"name"$: 3}
{\("na" + "me"): 3}
```

### Constant properties

Furthermore, if the property is preceded with a `#`, it is treated as an unmodifiable property i.e. constant:

```lexem
{#name: 3}
{#"name": 3}
{#$"name"$: 3}
{#\("na" + "me"): 3}
```

This means the same as:

```lexem
var obj = {name: 3}
Object.freeze(property: "name", for: obj)
```

### Simplifications (syntactic sugar)

In addition to the previous patterns, objects allow other types of syntax to simplify its definition:

| Rule | Simplifies | When to replace |
|:----:|:----------:|:----------------|
|`value`|`value: value`|Whenever the property's name match with the variable's name used as the value.|
|`name() {}`|`name: fun() {}`|Whenever the expression is a function definition. Names can also be replaced by a string literal or escaped expression.|

Finally, the last pattern makes a property to have a getter (i.e. a function that is executed when retrieving its value) and/or a setter (i.e. a function that is executed when changing its value) instead of a plain value.

To do this it is necessary to use the following code:

```lexem
let obj = {}        #- an empty object.
let descriptor = {  #- the object descriptor.
    value: "Jhon",
    get() {
        return value
    },
    set(new_value) {
        value = new_value
    }
}

Object.define(property: "name", by: descriptor)

#- obj.name == "Jhon"
```

But a simplification is offered to implement this in an easier way:

```lexem
let obj = {
    name {
        value = "Jhon"
        get() {
            return value
        }
        set(new_value) {
            value = new_value
        }
    }
}

#- obj.name == "Jhon"
```

> **Note**: descriptors only allow three properties, all of them optional: `value`, `get` and `set`, being the former of any type and the lasts of `function` type.

### Property-style object definition

There is another way to define an object called _property-style_ because it is generally used to create _properties_ in nodes.

In this mode, objects are defined with the following syntax:

```lexem
@[active - deactive : set(value)]  #- normal
@#[active - deactive : set(value)] #- constant  
```

Which is translated to:

```lexem
{
    active: true,
    deactive: false,
    set: value
}
#{
    active: true,
    deactive: false,
    set: value
}
```

Following these rules:

- All properties at the beginning are set to `true`.
- All properties after the `-` are set to `false`.
- All properties after the `:` require an expression which is its value.

## Map types

Represents a no-ordered group of key-value pairs, with the ability to index by keys. It differs from common objects in that the keys can be any type, not only `String`s.

- Type: `Map`
- Prototype: `Map.prototype`.
- Literals:

  | Literal | Meaning |
  |:-------:|:--------|
  |`map!{}`|An empty object.|
  |`map!{key0: value0, key1: value1}`|A constant map filled with key-value pairs.|
  |`map!#{name0: value0, name1: value1}`|A constant map filled with key-value pairs. They can't be changed and the map can't be extended or shrunk.|

> **Note**: values could be complex expressions and of any type.

## Function type

Represents an object with the ability to execute *functional* code.

- Type: `Function`
- Prototype: `Function.prototype`.
- Literals:

  | Literal | Meaning |
  |:-------:|:--------|
  |`fun{body}`|Anonymous function definition without arguments.|
  |`fun(args){body}`|Anonymous function definition.|
  |`fun name{body}`|Named function definition without arguments. It can only be used as an statement.|
  |`fun name(args){body}`|Named function definition. It can only be used as an statement.|

```lexem
let function = fun(arg0: value0, arg1: value1) {}
```

Arguments are a list of key-value pairs separated with commas (`,`).

## Expression type

Represents an object with the ability to execute *functional* and *descriptive* code that analyze the textual or binary input.

- Type: `Expression`
- Prototype: `Expression.prototype`.
- Literals:

  | Literal | Meaning |
  |:-------:|:--------|
  |`exp{body}`|Anonymous expression definition without arguments.|
  |`exp(args){body}`|Anonymous expression definition.|
  |`exp name{body}`|Named expression definition without arguments. It can be only used as an statement.|
  |`exp name(args){body}`|Named expression definition. It can be only used as an statement.|

> **Note**: see 'descriptive expressions' section to know more information about expressions.
