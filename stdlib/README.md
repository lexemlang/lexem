# Table of contents

- [Table of contents](#table-of-contents)
- [Lexem's standard library](#lexems-standard-library)
  - [Types](#types)
  - [Prototypes](#prototypes)
  - [Global objects](#global-objects)

# Lexem's standard library

The standard library can be accessed from any context and its content is divided in three big sections:

## Types

Every valid type of Lexem has a global object (i.e. the Type) that holds global methods and properties of that type.

- [Any](types/any.md): any type
- [Nil](types/nil.md)
- [Logic](types/logic.md)
- [Integer](types/integer.md)
- [Float](types/float.md)
- [String](types/string.md)
- [Interval](types/interval.md)
- [BitList](types/bitList.md)
- [List](types/list.md)
- [Set](types/set.md)
- [Object](types/object.md)
- [Map](types/map.md)
- [Function](types/function.md)
- [Expression](types/expression.md)
- [Filter](types/filter.md)
- [Node](types/node.md)

## Prototypes

The objects that contains common properties and methods for every instance of a type. Somewhat like a class-static data. They are accessed through the types.

- [Any.prototype](prototypes/any.md): the root prototype from which all objects inherits direct or indirectly.
- [Nil.prototype](prototypes/nil.md)
- [Logic.prototype](prototypes/logic.md)
- [Integer.prototype](prototypes/integer.md)
- [Float.prototype](prototypes/float.md)
- [String.prototype](prototypes/string.md)
- [Interval.prototype](prototypes/interval.md)
- [BitList.prototype](prototypes/bitList.md)
- [List.prototype](prototypes/list.md)
- [Set.prototype](prototypes/set.md)
- [Object.prototype](prototypes/object.md)
- [Map.prototype](prototypes/map.md)
- [Function.prototype](prototypes/function.md)
- [Expression.prototype](prototypes/expression.md)
- [Filter.prototype](prototypes/filter.md)
- [Node.prototype](prototypes/node.md)

## Global objects

The rest of built-in elements of Lexem are packed in different global objects.

- [Math](globals/math.md)
- [Analyzer](globals/analyzer.md)
- [Debug](globals/debug.md)
- **Globals**: an empty object to share data across the whole code.
- **import**: the function that imports another _lexem_ file. See [Module imports](../specification/modules.md#imports) to get more information.
