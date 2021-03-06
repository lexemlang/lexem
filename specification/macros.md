
# Table of contents

- [Table of contents](#table-of-contents)
- [Macros](#macros)
  - [check_props!](#check_props)
  - [line!](#line)
  - [file!](#file)
  - [directory!](#directory)
  - [file_content!](#file_content)
  - [backtrack!](#backtrack)

# Macros

## check_props!

| As functional expression | As statement | As lexeme |
|:------------------------:|:------------:|:---------:|
| Yes                      | Yes          | Yes       |

Using the same syntax of the _Property-style object definition_, checks whether the generated object match with the properties object inside the current node, returning a logic value.

For example:

```lexem
-- As functional expression or statement.
check_props![active - deactive : with(value)]

-- As lexeme.
|> check_props![active]
```

Is equivalent to:

```lexem
-- As functional expression or statement.
(node.properties.active == true and node.properties.deactive == false and node.properties.with == value)

-- As lexeme.
|> \(? node.properties.active == true)
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

Returns a `String` with the content of the current file.

For example:

```lexem
let x = file_content!
var y = 3
```

Is equivalent to:

```lexem
let x = "let x = file_content!\nvar y = 3"
var y = 3
```

## backtrack!

| As functional expression | As statement | As lexeme |
|:------------------------:|:------------:|:---------:|
| Yes                      | Yes          | Yes       |

Initiates the backtracking, optionally sending a value to indicate why the error was thrown.

For example:

```lexem
-- As functional expression or statement.
var x = argument || backtrack!(expression)
var x = argument || backtrack!

-- As lexeme.
|> "abc" backtrack!(expression)
|> "abc" backtrack!
```

Is equivalent to:

```lexem
-- As functional expression or statement.
var x = argument || Analyzer.initBacktrack(expression)
var x = argument || Analyzer.initBacktrack(nil)

-- As lexeme.
|> "abc" \(Analyzer.initBacktrack(expression))
|> "abc" \(Analyzer.initBacktrack(nil))
```

|> **Note**: if the value is not specified a `nil` is thrown.
