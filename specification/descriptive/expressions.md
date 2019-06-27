
# Index

- [Index](#index)
- [Descriptive expressions](#descriptive-expressions)
    - [Properties](#properties)
        - [Built-in properties](#built-in-properties)
    - [Body](#body)
        - [Static pattern](#static-pattern)
        - [Optional pattern](#optional-pattern)
        - [Negative pattern](#negative-pattern)
        - [Alternative pattern](#alternative-pattern)
        - [Additive pattern](#additive-pattern)
        - [Selective pattern](#selective-pattern)
        - [Quantified pattern](#quantified-pattern)
    - [Nodes](#nodes)

# Descriptive expressions

The descriptive expressions define how *Lexem* should analise and capture the textual or binary input.

An expression is composed by:

1. **Expression**: the whole block of descriptive and functional code. It is similar to functions.
2. **Patterns**: sets of lexemes that are executed atomically and that follow a specific behaviour.
3. **Lexemes**: the minimum executing unit of the descriptive core of *Lexem*. Each of them has its own syntax and meaning.

> *Lexem* receives its name from its minimum executing unit, i.e. the lexemes.

Like functions in the functional core, expressions have two sections:

- **Header**: define how the analyzer should act when processing this expression.
- **Body**: where the code and patterns are set.

An example of fully defined expression is the following:

```lexem
#- Header
exp(args) {
    #- Body
    |> "Hola mundo"
}
```

Arguments are a list of key-value pairs separated with commas (`,`).

## Properties

Expressions have one default argument called `props` that contains all the properties of the expression. It is the first argument of all expressions. With this, the caller can overwrite the properties of an expression to dynamically change the behaviour of an expression.

To set the default properties of an expression the following syntax must be used:

```lexem
exp(props: props![prop], arg1, ...) {}
```

But this style is so common that can be written in a simpler way:

```lexem
exp(props![prop], arg1, ...) {}
```

With this style is compulsory that the props will be the first element in the arguments list.

Finally, to call an expression it should use the following scheme:

```lexem
var expr = exp(props![prop], arg1: value1, ...) {}

expr(props![prop], arg1: value1, ...)
```

### Built-in properties

There are a group of built-in properties that expressions use to change their behaviour:

| Property | Meaning |
|:--------:|:--------|
| `capture` | Makes the expression capturable, i.e. the expression generates a node with its content in its parent. |
| `children` | Allows to keep its child nodes. If `capture` is `false` and this is `true`, children will hang directly from the parent of this node. |
| `property` | Generates a property in the parent node with the name of the expression whose value is the captured content of the expression. If this property receives a `String` instead of a `Logic`, the generated property will be named with that value. |
| `insensible` | Tells the capturing lexemes whether to interpret uppercase and lowercase as the same. |
| `backtrack` | Specifies if the backtracking should enter to the expression to look for another option.|
| `error` | Specifies if an error is thrown inside the expression, it should start the backtracking instead of finishing the analysis.|
| `reverse` | Tells the analyzer to capture the input in the normal way (left to right) or in the reverse one (right to left) from the current position. |
| `consume` | Specifies if the expression should consume the input or just ends where it begins. |

The properties are automatically set to the following values if they are not overwritten in the call or by an explicit default value:

```lexem
[capture children backtrack consume - property insensible error reverse]
```

## Body

The body of an expression is composed by descriptive and functional code.

All descriptive code must be started with a `|` which in fact creates a pattern and optionally a union, which groups patterns under the same behaviour thanks to a common identifier.

Depending on those concepts we have:

1. **Single patterns**: those that work alone without joining into a union.
2. **Patterns with union**: patterns that collaborate with other patterns of the same type. They are divided into:
    1. **Master patterns**: always generate an union and allows others to join to it.
    2. **Slave patterns**: never generate an union, but they are able to join others.

### Static pattern

It is a single pattern that imposes that its lexemes are always captured, so if any of them fail, the backtracking is started.

```lexem
|> lexemes
```

### Optional pattern

It is a single pattern that imposes that its lexemes can be skipped to be captured, so if any of them fail, the whole pattern is omitted and continues with normal execution.

```lexem
|? lexemes
```

### Negative pattern

It is a single pattern that imposes that its lexemes should never be captured, so if any of them fail, the whole pattern is omitted and continues with normal execution, but if they all match, backtracking is started.

```lexem
|! lexemes
```

### Alternative pattern

It is a pattern with union that requires that only one of the patterns that are associated with the same union matches, so if no one of them match, the backtracking is started. Once one of them match, the rest are skipped.

```lexem
| unionName > lexemes
```

The union section in optional (`unionName >`).

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

It is a pattern with union that requires that at least one of the patterns that are associated with the same union matches, so if no one of the match backtracking is started. Once one matches the rest that does not match are skipped.

```lexem
|+ unionName > lexemes
```

The union section in optional (`unionName >`).

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

It is a pattern with union that requires that just only one of the patterns that are associated with the same union matches or none of them, so never starts the backtracking. Once one matches the rest that are skipped.

```lexem
|* unionName > lexemes
```

The union section in optional (`unionName >`).

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

Every expression generates at the beginning a node in the *Token tree* which contains all the captured content.

These nodes are under the rules of capturing controlled by the `capture` and `children` properties.

Moreover, this nodes also can be part of another result tree called *Semantic tree* which contains only useful nodes in a structural way.

For example, the *Token tree* can have all comments of a code, while those are stripped from the *Semantic tree* due to not having semantic meaning.
