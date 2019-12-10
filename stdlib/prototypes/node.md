
# Table of contents

- [Table of contents](#table-of-contents)
- [Methods](#methods)
  - [.toString() -&gt; String](#tostring--gt-string)
- [Properties](#properties)
  - [.name -&gt; String](#name--gt-string)
  - [.from -&gt; Integer](#from--gt-integer)
  - [.to -&gt; Integer | Nil](#to--gt-integer-nil)
  - [.parent -&gt; Node | Nil](#parent--gt-node-nil)
  - [.children -&gt; List&lt;Node&gt;](#children--gt-listltnodegt)
  - [.properties -&gt; Object](#properties--gt-object)

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
