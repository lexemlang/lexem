
# Index

- [Index](#Index)
- [Descriptive expressions](#Descriptive-expressions)
  - [Parameters](#Parameters)
  - [Properties](#Properties)
    - [Built-in properties](#Built-in-properties)
  - [Body](#Body)
    - [Static pattern](#Static-pattern)
    - [Optional pattern](#Optional-pattern)
    - [Negative pattern](#Negative-pattern)
    - [Alternative pattern](#Alternative-pattern)
    - [Additive pattern](#Additive-pattern)
    - [Selective pattern](#Selective-pattern)
    - [Quantified pattern](#Quantified-pattern)
  - [Nodes](#Nodes)

# Descriptive expressions

The descriptive expressions define how _Lexem_ should analise and capture the textual or binary input.

An expression is composed by:

1. **Expression**: the whole block of descriptive and functional code. It is similar to functions.
2. **Patterns**: sets of lexemes that are executed atomically and that follow a specific behaviour.
3. **Lexemes**: the minimum executing unit of the descriptive core of _Lexem_. Each of them has its own syntax and meaning.

> _Lexem_ receives its name from its minimum executing unit, i.e. the lexemes.

Like functions in the functional core, expressions have two sections:

- **Header**: define how the analyzer should act when processing this expression.
- **Body**: where the code and patterns are set.

An example of fully defined descriptive expression statement is the following:

```lexem
#- Header
exp expressionName[properties](parameters) {
    #- Body
    |> "Hello world"
}
```

If it is used inside a functional expression, it requires a name to generate a node but does not generate a variable as the statement do.

## Parameters

The parameters are a list of identifiers separated with commas (`,`), optionally with a default value:

```lexem
#- no params
exp() { }

#- no defaults
exp(param1, param2, param3) { }

#- with defaults
exp(param1: true, param2: "x") { }

#- mixed
exp() { }
```

There is a default property called `props` that reference to the properties, so if you want more control over how to define a property,
use `exp(parameters, props: properties)` instead of `exp[properties](parameters)`.

> **Note**: if there is no parameters, the whole block can be omitted, including the parenthesis `()`.

## Properties

The properties of an expression are set inside the block delimited by square brackets `[]`.

> **Note**: if there is no properties, the whole block can be omitted, including the square brackets `[]`.

### Built-in properties

There are a group of built-in properties that expressions use to change their behaviour:

| Property | Meaning |
|:--------:|:--------|
| `capture` | Captures the expression, i.e. the expression generates a node with its content in its parent. |
| `children` | Allows to keep its child nodes. If `capture` is `false` and this is `true`, children will hang directly from the parent of this node. |
| `property` | Generates a property in the parent node with the name of the expression whose value is the captured content of the expression. If this property receives a `String` instead of a `Logic`, the generated property will be named with that value. |
| `insensible` | Tells the capturing lexemes whether to interpret uppercase and lowercase as the same. |
| `backtrack` | Specifies if the backtracking should enter to the expression to look for another option.|
| `error` | Specifies if an error is thrown inside the expression, it should start the backtracking instead of finishing the analysis.|
| `reverse` | Tells the analyzer to capture the input in the normal way (left to right) or in the reverse one (right to left) from the current position. |
| `consume` | Specifies if the expression should consume the input or just ends where it begins. |
| `over` | This properSpecifies if the expression should consume the input or just ends where it begins. |

The properties are automatically set to the following values if they are not overwritten in the call or by an explicit default value:

```lexem
[capture children consume - property insensible backtrack error reverse]
```

There is also another property that makes the expression to be executed over the content already captured by a node called `over`.
This property generates new nodes that will replace the specified node.

## Body

The body of an expression is composed by descriptive and functional code.

All descriptive code must be started with a `|` which in fact creates a pattern and optionally a union, which groups patterns under the same behaviour thanks to a common identifier.

Depending on those concepts we have:

1. **Single patterns**: those that work alone without joining into a union.
2. **Patterns with union**: patterns that collaborate with other patterns of the same type. They are divided into:
    1. **Master patterns**: always generate an union and allows others to join to it.
    2. **Slave patterns**: never generate an union, but they are able to join others.

### Static pattern

This is a single pattern which requires that all of its lexemes must be always captured, i.e. if any of them fail, the backtracking is started.

```lexem
|> lexemes
```

It is used to capture static grammar sections, for example:

```lexem
#- a number
|> [0..9]

#- a letter
|> [a..z A..Z]
```

### Optional pattern

Like _Static patterns_, this is a single pattern that imposes that all of its lexemes must be always captured, but on the contrary, if any of them fail, the whole pattern is skipped and continues with the normal execution.

```lexem
|? lexemes
```

It is used to optionally capture static grammar sections, for example:

```lexem
#- a word and a number with optionally a dash (-) between them
|> [a..z A..Z]+
|? "-"
|> [0..9]
```

### Negative pattern

It is a single pattern that requires that any of the inner lexemes must fail, so if any of them fail, the whole pattern is skipped and continues with normal execution, but if they all match, the backtracking is started.

```lexem
|! lexemes
```

It is used to prevent an specific pattern in a certain position, for example:

```lexem
#- a number not followed by a letter
|> [0..9]+
|! [a..z A..Z]
```

### Alternative pattern

This is a pattern that joins to a union and requires that only one of the patterns that are associated with the union matches, so if no one of them match, the backtracking is started. All patters that do not match are skipped and once one of them match, the rest are skipped.

```lexem
| unionName > lexemes
```

The union section in optional (`unionName >`).

It is used to capture two or more options alternatively, i.e. choosing just one of them, for example:

```lexem
#- two words separated by a dash (-) or a whitespace
|> [a..z A..Z]+
|  "-"
|  " "
|> [a..z A..Z]+
```

> **Note**: alternative patterns are equivalent to be part of an union whose quantifier is `{1}`. In case there is only one pattern associated with the union it works like an static pattern.

The first pattern acts like master generating the union and the rest of them work like slaves:

- An anonymous pattern (master) followed by one or more slave patterns forming an anonymous union.

    ```lexem
    |   #- Master 1
    |   #- Slave  1.1
    |   #- Slave  1.2
    |>  #- Interruption
    |   #- Master 2
    ```

- A master pattern with union followed by one or more patterns, at any position of the code, with the same union name belong to the same union.

    ```lexem
    |a>     #- Master a
    |> {
        |a> #- Slave  a.1
    }
    |a>     #- Slave  a.2
    ```

- Take into account that patterns with named unions can't be joined to anonymous patterns:

    ```lexem
    |a> #- Master a
    |   #- Master 1
    |   #- Slave  1.1
    |a> #- Slave  a.1
    |a> #- Slave  a.2
    |   #- Master 2
    ```

### Additive pattern

The same as the _Alternative pattern_, this joins a union and requires that at least one of the patterns that are associated with the union matches, so if no one of the match backtracking is started. All patters that do not match are skipped.

```lexem
|+ unionName > lexemes
```

The union section in optional (`unionName >`).

It is used to capture optionally a set of options but ensuring that at least one of them is capture, for example:

```lexem
#- capture an integer (5), an integer and a decimal part (5.4), or just the decimal part (.4)
|+ [0..9]+
|+ "." [0..9]+
```

> **Note**: additive patterns are equivalent to be part of an union whose quantifier is `{1,}`. In case there is only one pattern associated with the union it works like an static pattern.

The first pattern acts like master generating the union and the rest of them work like slaves:

- An anonymous pattern (master) followed by one or more slave patterns forming an anonymous union.

    ```lexem
    |+  #- Master 1
    |+  #- Slave  1.1
    |+  #- Slave  1.2
    |>  #- Interruption
    |+  #- Master 2
    ```

- A master pattern with union followed by one or more patterns, at any position of the code, with the same union name belong to the same union.

    ```lexem
    |+a>        #- Master a
    |> {
        |+a>    #- Slave  a.1
    }
    |+a>        #- Slave  a.2
    ```

- Take into account that patterns with named unions can't be joined to anonymous patterns:

    ```lexem
    |+a>    #- Master a
    |+      #- Master 1
    |+      #- Slave  1.1
    |+a>    #- Slave  a.1
    |+a>    #- Slave  a.2
    |+      #- Master 2
    ```

### Selective pattern

It is a pattern that joins to a union and requires that just only one of the patterns that are associated with the union matches or none of them, so never starts the backtracking. Once one pattern matches, the rest that are skipped.

```lexem
|* unionName > lexemes
```

The union section in optional (`unionName >`).

It is used to capture optionally just one of the patterns of the union, for example:

```lexem
#- capture an "a", a "b" or nothing.
|* "a"
|* "b"
```

> **Note**: selective patterns are equivalent to be part of an union whose quantifier is `{0,1}`. In case there is only one pattern associated with the union it works like an optional pattern.

The first pattern acts like master generating the union and the rest of them work like slaves:

- An anonymous pattern (master) followed by one or more slave patterns forming an anonymous union.

    ```lexem
    |*  #- Master 1
    |*  #- Slave  1.1
    |*  #- Slave  1.2
    |>  #- Interruption
    |*  #- Master 2
    ```

- A master pattern with union followed by one or more patterns, at any position of the code, with the same union name belong to the same union.

    ```lexem
    |*a>        #- Master a
    |> {
        |*a>    #- Slave  a.1
    }
    |*a>        #- Slave  a.2
    ```

- Take into account that patterns with named unions can't be joined to anonymous patterns:

    ```lexem
    |*a>    #- Master a
    |*      #- Master 1
    |*      #- Slave  1.1
    |*a>    #- Slave  a.1
    |*a>    #- Slave  a.2
    |*      #- Master 2
    ```

### Quantified pattern

It is a pattern with union that requires that at least the number of the patterns specified in its quantifier match but not exceeding the maximum, so if minimum is not matched, the backtracking is started. Once the maximum is reached the rest are skipped.

```lexem
|{x, y} unionName > lexemes
|{} unionName > lexemes
```

The union section in optional (`unionName >`).

It is used to explicitly set the minimum and maximum number of patterns of the union, for example:

```lexem
#- capture one of: "a", "b", "c", "ab", "bc", "ac"
|{1,2} "a"
|{} "b"
|{} "c"
```

Moreover, the fist syntax is masters while the second is the for slaves, so there are syntactic differences between them that allow us not to confuse them:

- An anonymous pattern (master) followed by one or more slave patterns forming an anonymous union.

    ```lexem
    |{x,y}  #- Master 1
    |{}     #- Slave  1.1
    |{}     #- Slave  1.2
    |>      #- Interruption
    #- |{}  #- Error because it has no master.
    |{x,y}  #- Master 2
    ```

- A master pattern with union followed by one or more patterns, at any position of the code, with the same union name belong to the same union.

    ```lexem
    |{x,y}a>    #- Master a
    |> {
        |{}a>   #- Slave  a.1
    }
    |{}a>       #- Slave  a.2
    ```

- Take into account that patterns with named unions can't be joined to anonymous patterns:

    ```lexem
    |{x,y}a>    #- Master a
    |{}         #- Master 1
    |{}         #- Slave  1.1
    |{x,y}a>    #- Slave  a.1
    |{x,y}a>    #- Slave  a.2
    |{}         #- Master 2
    ```

## Nodes

The result of the analysis is a tree of nodes, each one representing a section of the grammar that has meaning by itself. Thus, every expression at the beginning of its execution generates a node in the result tree which contains all the captured content.

Those nodes are under the rules of capturing controlled by the `capture` and `children` properties.
