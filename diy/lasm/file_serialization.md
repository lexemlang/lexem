# Index

- [Index](#Index)
- [File serialization](#File-serialization)
  - [`List<?>`](#List)
  - [`String`](#String)
  - [`BitList`](#BitList)
  - [`Interval`](#Interval)
  - [`Function`](#Function)
  - [`Expression`](#Expression)
  - [`Filter`](#Filter)

# File serialization

- **Module path** (`String`): the path of the module. It will be imported from that path.
- **Constants**
    - **Strings** (`List<String>`)
        - The first `String`, i.e. at the `0` index, must be an empty one (length equal to 0).
    - **BitLists** (`List<BitList>`)
        - The first `BitList`, i.e. at the `0` index, must be an empty one (length equal to 0).
    - **Intervals** (`List<Interval>`)
- **Program**
    - **Functions** (`List<Function>`): the code of each function.
    - **Expressions** (`List<Expression>`): the code of each expression.
    - **Filters**: (`List<Filter>`): the code of each filter.
    - **Module**: the code of the module preceded by an `Integer` specifying the number of bytes for the code.
    
> **Note**: all `Integer` values are 64-bit length.

> **Note 2**: all values are written in big endian.

## `List<?>`

- **Size** (`Integer`): the total number of bytes of the whole `List`.
- **Count** (`Integer`): the number of elements inside the `List`.
- **Content**: the content of the `List`.

## `String`

- **Size** (`Integer`): the length of the `String` in bytes.
- **Count** (`Integer`): the length of the `String` in characters.
- **Content**: the content of the `String`.

## `BitList`

- **Size** (`Integer`): the length of the `BitList` in bytes.
- **Count** (`Integer`): the length of the `BitList` in bits.
- **Content**: the content of the `BitList`.

## `Interval`

- **Size** (`Integer`): the length of the `Interval` in bytes.
- **Count** (`Integer`): the length of the `Interval` in ranges, each one containing two integers of 32-bit length.
- **Content**: the content of the `Interval`.

## `Function`

- **Size** (`Integer`): the number of bytes of the Function's code.
- **Code**: the code of the function.

## `Expression`

- **Size** (`Integer`): the number of bytes of the Expression's code.
- **Code**: the code of the expression.

## `Filter`

- **Size** (`Integer`): the number of bytes of the Filter's code.
- **Code**: the code of the filter.
