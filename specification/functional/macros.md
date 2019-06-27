
# Index

- [Index](#index)
- [Functional macros](#functional-macros)
    - [pattern!](#pattern)
    - [check_props!](#checkprops)
    - [logic_line!](#logicline)
    - [line!](#line)
    - [file!](#file)
    - [directory!](#directory)
    - [file_content!](#filecontent)

# Functional macros

## pattern!

Allows to easily create an expression with only one static pattern.

For example:

```lexem
let x = pattern!(lexemes)
```

Is equivalent to:

```lexem
let x = exp() { |> lexemes }
```

## check_props!

Using the same syntax of the *Property-style object definition*, checks if the generated object match with the properties object inside the current node, returning a logic value.

For example:

```lexem
#- Functional code.
check_props![active - deactive : with(value)]

#- Descriptive code.
|> check_props![active]
```

Is equivalent to:

```lexem
#- Functional code.
(node.properties.active == true and node.properties.deactive == false and node.properties.with == value)

#- Descriptive code.
|> \(? node.properties.active == true)
```

## logic_line!

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

Returns an `Integer` with the line number in which it appears inside the current file.

## file!

Returns a `String` value that contains the absolute path of the current file from the root of the project.

## directory!

Returns a `String` value that contains the absolute path of the current directory from the root of the project.

## file_content!

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