
# Index

- [Index](#Index)
- [Functional macros](#Functional-macros)
  - [check_props!](#check_props)
  - [logic_line!](#logic_line)
  - [line!](#line)
  - [file!](#file)
  - [directory!](#directory)
  - [file_content!](#file_content)
  - [backtrack!](#backtrack)

# Functional macros

## check_props!

| As functional expression | As statement | As lexeme |
|:------------------------:|:------------:|:---------:|
| Yes                      | Yes          | Yes       |

Using the same syntax of the _Property-style object definition_, checks whether the generated object match with the properties object inside the current node, returning a logic value.

For example:

```lexem
#- As functional expression or statement.
check_props![active - deactive : with(value)]

#- As lexeme.
|> check_props![active]
```

Is equivalent to:

```lexem
#- As functional expression or statement.
(node.properties.active == true and node.properties.deactive == false and node.properties.with == value)

#- As lexeme.
|> \(? node.properties.active == true)
```

## logic_line!

| As functional expression | As statement | As lexeme |
|:------------------------:|:------------:|:---------:|
| Yes                      | No           | No        |

Returns an `Object` with the line numbers in which it appears inside the current file.

For example:

```lexem
1. let x = logic_line!
2. let y = logic_line! +
3. x *
4. y
```

Is equivalent to:

```lexem
let x = {from: 1, to: 1}
let y = {from: 2, to: 4}
```

## line!

| As functional expression | As statement | As lexeme |
|:------------------------:|:------------:|:---------:|
| Yes                      | No           | No        |

Returns an `Integer` with the line number in which it appears inside the current file.

For example:

```lexem
...
25. let line = line!
...
```

Is equivalent to:

```lexem
...
25. let line = 25
...
```

## file!

| As functional expression | As statement | As lexeme |
|:------------------------:|:------------:|:---------:|
| Yes                      | No           | No        |

Returns a `String` value that contains the absolute path of the current file from the root of the project.

For example, in `path/to/file.lxm`:

```lexem
let file = file!
```

Is equivalent to:

```lexem
let file = "path/to/file.lxm"
```

## directory!

| As functional expression | As statement | As lexeme |
|:------------------------:|:------------:|:---------:|
| Yes                      | No           | No        |

Returns a `String` value that contains the absolute path of the current directory from the root of the project.

For example, in `path/to/file.lxm`:

```lexem
let file = file!
```

Is equivalent to:

```lexem
let file = "path/to/"
```

## file_content!

| As functional expression | As statement | As lexeme |
|:------------------------:|:------------:|:---------:|
| Yes                      | No           | No        |

Returns a `String` with the content of the indicated lines of the current file.

For example:

```lexem
1. let x = line_content!(from: 1, to: 2)
2. let y = line_content!(..logic_line!) +
3. x *
4. y
```

Is equivalent to:

```lexem
let x = "let x = line_content!(from: 1, to: 2)\nvar! y = line_content!(line!) +"
let y = "let y = line_content!(line!) +\nx *\ny"
```

## backtrack!

| As functional expression | As statement | As lexeme |
|:------------------------:|:------------:|:---------:|
| Yes                      | Yes          | Yes       |

Initiates the backtracking.

For example:

```lexem
#- As functional expression or statement.
var x = argument || backtrack!

#- As lexeme.
|> "abc" backtrack!
```

Is equivalent to:

```lexem
#- As functional expression or statement.
var x = argument || Analyzer.initBacktrack()

#- As lexeme.
|> "abc" !""
```
