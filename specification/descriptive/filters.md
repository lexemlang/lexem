
# Index

- [Index](#Index)
- [Filters](#Filters)
  - [Parameters](#Parameters)
  - [Properties](#Properties)
    - [Built-in properties](#Built-in-properties)
  - [Body](#Body)
  - [Nodes](#Nodes)

# Filters

A filter is an element like an expression or a function that a performs an analysis over the result tree.
They receive a previously generated node and catch those child nodes that match the specified selectors, also manually adding new nodes.

A filter is composed by:

1. **Filter**: the whole block of descriptive and functional code. It is similar to expressions.
2. **Patterns**: sets of lexemes that are executed atomically and that follow a specific behaviour.
3. **Filter lexemes**: the minimum executing unit of the descriptive core of *Lexem* that filter nodes. Each of them has its own syntax and meaning.

Like functions in the functional core, filters have two sections:

- **Header**: define how the analyzer should act when processing this filter.
- **Body**: where the code and patterns are set.

An example of fully defined filter statement is the following:

```lexem
#- Header
filter filterName[properties](parameters) {
    #- Body
    |> @(*)
}
```

While if it is used inside a functional expression, it does not allow the name:

```lexem
#- Header
filter[properties](parameters) {
    #- Body
    |> @(*)
}
```

## Parameters

The parameters are a list of identifiers separated with commas (`,`), optionally with a default value:

```lexem
#- no params
filter() { }

#- no defaults
filter(param1, param2, param3) { }

#- with defaults
filter(param1: true, param2: "x") { }

#- mixed
filter() { }
```

> **Note**: the parenthesis of the parameters are always required.

## Properties

The properties of a filter are set inside the block delimited by square brackets `[]`.

> **Note**: if there is no properties, the whole block can be omitted, including the square brackets `[]`.

### Built-in properties

There are a group of built-in properties that filters use to change their behaviour:

| Property | Meaning |
|:--------:|:--------|
| `capture` | Captures the filter, i.e. the filter generates a node in its parent node. |
| `children` | Allows to keep its child nodes. If `capture` is `false` and this is `true`, children will hang directly from the parent of this node. |
| `backtrack` | Specifies if the backtracking should enter to the filter to look for another option. |
| `error` | Specifies if an error is thrown inside the expression, it should start the backtracking instead of finishing the analysis. |
| `reverse` | Tells the analyzer to capture the input in the normal way (left to right) or in the reverse one (right to left) from the current position. |
| `consume` | Specifies whether the filter should consume the nodes or just ends where it begins. |

The properties are automatically set to the following values if they are not overwritten in the call or by an explicit default value:

```lexem
[capture children backtrack consume - error reverse]
```

## Body

The body uses the same patterns of descriptive expressions. See [expressions](expressions.md#Body) for more details.

## Nodes

The result of the analysis is a new tree of nodes that replace the one that has been passed as input.
