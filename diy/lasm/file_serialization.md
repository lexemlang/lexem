# Index

- [Index](#Index)
- [File serialization](#File-serialization)
  - [String](#String)
  - [BitList](#BitList)
  - [Interval](#Interval)
  - [List](#List)

# File serialization

- **Module name** (`String`): the name of the module. It will be imported from that name.
- **String constants** (`List<String>`)
- **BitList constants** (`List<BitList>`)
- **Interval constants** (`List<Interval>`)
- **Program**: the code of the module.

## String

- **Size** (`Integer`): the length of the `string`.
- **Content**: the content of the `string`.

## BitList

- **Size** (`Integer`): the length of the `BitList` in bytes.
- **BitSize** (`Integer`): the length of the `BitList` in bits.
- **Content**: the content of the `BitList`.

## Interval

- **Size** (`Integer`): the number of ranges inside the `Interval`.
- **Content**: the content of the `Interval`.

## List

- **Size** (`Integer`): the number of elements in the list.
- **Content**: the content of the list.
