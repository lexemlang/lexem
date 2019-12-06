
# Table of contents

- [Table of contents](#table-of-contents)
- [Methods](#methods)
  - [`.toString() -> String`](#tostring---string)
- [Properties](#properties)
  - [`.name -> String`](#name---string)
  - [`.from -> Integer`](#from---integer)
  - [`.to -> Integer | Nil`](#to---integer-nil)
  - [`.parent -> Node | Nil`](#parent---node-nil)
  - [`.children -> List<Node>`](#children---listnode)
  - [`.properties -> Object`](#properties---object)

# Methods

## `.toString() -> String`

Returns a `String` representing the logic value.

```lxm
logic.toString()
```

### Errors

- **`BadThisArgumentTypeError`**: when this function is invoked on a value that is not a `Nil`.

### Examples

```lxm
Debug.log(node.toString())   -- "[name, childs: 3, properties: 5]"
```

# Properties

## `.name -> String`

The name of the node.

```lxm
node.name
```

## `.from -> Integer`

The start position of the node over the textual input.

```lxm
node.from
```

## `.to -> Integer | Nil`

The end position of the node over the textual input. If it is not finished, this property returns `nil`.

```lxm
node.to
```

## `.parent -> Node | Nil`

The parent `node`. If it is the root node, this property returns `nil`.

```lxm
node.parent
```

## `.children -> List<Node>`

A list containing the children of the node.

```lxm
node.children
```

## `.properties -> Object`

An object containing the properties of the node.

```lxm
node.properties
```
