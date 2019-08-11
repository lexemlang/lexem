
# Index

- [Index](#index)
- [Lexemes](#lexemes)
  - [Literal texts](#literal-texts)
  - [Literal binary sequence](#literal-binary-sequence)
  - [Character blocks](#character-blocks)
  - [Groups](#groups)
    - [Header](#header)
      - [Alternation type](#alternation-type)
      - [Properties](#properties)
  - [Quantifiers](#quantifiers)
    - [Greedy quantifiers](#greedy-quantifiers)
    - [Lazy quantifiers](#lazy-quantifiers)
  - [Quantified groups](#quantified-groups)
  - [Anchors](#anchors)
    - [Relative anchors](#relative-anchors)
    - [Absolute anchors](#absolute-anchors)
  - [Property modifier](#property-modifier)
  - [Accesses](#accesses)
    - [Re-parsing](#re-parsing)
    - [Filtering](#filtering)
  - [Executor (Embed functional code)](#executor-embed-functional-code)
  - [Continuation](#continuation)
  - [Data capturing](#data-capturing)
  - [Semantic re-naming](#semantic-re-naming)

# Lexemes

Lexemes are the minimum descriptive piece of code that has its own meaning, syntax and functionality.

There are two types of lexemes, those that define what content should be capture when the lexeme is executed and those that only change the flow of the analyzer.

## Literal texts

This type of lexeme captures literal textual patterns.

```lexem
!"text"ir-ir!ir
```

The syntax is divided in:

- **Negation**: tells the analyzer it is required that the lexeme does _NOT_ match to continue with the normal flow. It is used to know that a specific text is not present at the current position.
- **Text**: the content itself. It can be any of the string literals.
- **Properties**: the `insensible` and `reverse` properties are inherit from the expression or group that contains this lexeme, but they can be manually set for each lexeme. With the abbreviation got activated, deactivated when is preceded with a minus (`-`) or negate the inherit value if they are preceded with a (`!`).

Strings are evaluated in short-circuit mode, therefore if a previous section does not match, the followings are not evaluated. For example, in `"a\(b)c"`, if `"a"` does not match, the `\(b)` section is not evaluated, neither `"c"`.

> **Note**: the `insensible` and `reverse` properties are applied after evaluate an escaped expression.

## Literal binary sequence

This type of lexeme captures literal binary patterns.

```lexem
!0b"content"r-r!r
```

The syntax is divided in:

- **Negation**: tells the analyzer it is required that the lexeme does _NOT_ match to continue with the normal flow. It is used to know that a specific binary pattern is not present at the current position.
- **Text**: the content itself. It can be any of the `BitList` literals.
- **Properties**: the `reverse` property is inherit from the expression or group that contains this lexeme, but it can be manually set for each lexeme. With the abbreviation got activated, deactivated when is preceded with a minus (`-`) or negate the inherit value if they are preceded with a (`!`).

Binary patterns are evaluated in short-circuit mode, therefore if a previous section does not match, the followings are not evaluated. For example, in `0b"1001 \(b) 100"`, if `"1001"` does not match, the `\(b)` section is not evaluated, neither `"100"`.

## Character blocks

This type of lexemes capture just only one character alternatively between those that are inside of its body. Their syntax is like:

```lexem
![characters]ir-ir!ir
!itv[characters]ir-ir!ir
```

The syntax is divided in:

- **Negation**: tells the analyzer it is required that the lexeme does _NOT_ match to continue with the normal flow. It is used to know that a specific character is not present at the current position.
- **Characters**: the content itself. It can be any of the interval literals. The `uitv![]` literal can be abbreviated removing `uitv!`.
- **Properties**: the `insensible` and `reverse` properties are inherit from the expression or group that contains this lexeme, but they can be manually set for each lexeme. With the abbreviation got activated, deactivated when is preceded with a minus (`-`) or negate the inherit value if they are preceded with a (`!`).

> **Note**: after evaluate an escaped expression, the `insensible` and `reverse` property is applied to it.

## Groups

Groups are containers that join other lexemes to work with them in an atomic way. Moreover, groups can have a header like expressions to quickly create nodes and properties with the content. Finally, like patterns, groups have their own functionality allowing alternation with (`|`).

```lexem
!(header: option | option)
```

The negation tells the analyzer it is required that the lexeme does _NOT_ match to continue with the normal flow.

### Header

Group headers are similar to expression's.

```lexem
quantifier groupName [properties]
```

For example:

```lexem
(name[capture]: a | b)
(+[- error]: a | b)
({2,}: a | b | c)
([capture]: a | b | c)
```

The group name is used to create its associated node.

#### Alternation type

The quantifier of the header defines how the alternation works inside the group. Like anonymous patterns, they define an anonymous union.

By default, the union is alternative (`{1}`) but there are other types:

| Union | Quantifier | Meaning |
|:-----:|:----------:|:--------|
| Alternative | nothing or `{1}` | Only captures one of its options. If there is only one option, it works like a static union. |
| Additive | `+` or `{1,}` | Captures at least one option. If there is only one option, it works like a alternative union. |
| Quantified | `{x,y}` | Capture at least `x` options and less or equal than `y` options. |

#### Properties

There are a group of built-in properties that groups use to change their behaviour:

| Property | Meaning |
|:--------:|:--------|
| `capture` | Makes the group catchable, i.e. the group generates a node with its content in its parent. |
| `property` | Generates a property in the parent node with the name of the group whose value is the captured content of the group. If this property receives a `String` instead of a `Logic`, the generated property will be named with that value. |
| `children` | Allows to keep its child nodes. If `capture` is `false` and this is `true`, children will hang directly from the parent of this node. |
| `insensible` | Tells the capturing lexemes whether to interpret uppercase and lowercase as the same. |
| `backtrack` | Specifies whether the backtracking should enter to the group to look for another option. |
| `error` | If an error is thrown inside the expression, specifies whether it should start the backtracking instead of finishing the analysis. |
| `reverse` | Tells the analyzer to capture the input in the normal way (left to right) or in the reverse one (right to left) from the current position. |
| `consume` | Specifies whether the expression should consume the input or just ends where it begins. |

The properties are automatically set to the following values if they are not overwritten:

```lexem
[children backtrack consume - capture property insensible error reverse]
```

## Quantifiers

Quantifiers are not self-sufficient lexemes but modifiers for others. Like loops, quantifiers repeat a group of lexemes to match them a fixed number of times.

```lexem
lexeme{min, max}
```

There are a few simplifications to write quantifiers:

- If the maximum is omitted (`{min}`), the quantifier will match exactly `min` times.
- If the maximum is omitted but the comma is still written (`{min,}`), the quantifier will match at least `min` times.
- If everything is written (`{min, max}`), the quantifier will match between `min` and `max` times. Both included.

Moreover, there are two kind of behaviours for quantifiers, _greedy_ and _lazy_ and a modification of both called _atomic_ in which the backtracking can't enter to them once the flow has exit.

### Greedy quantifiers

They will try to match as many times as they can before continuing the analysis.

| Rule | Syntax | Meaning |
|:----:|:------:|:--------|
| Interval | `{n}` | See the explanation above. |
| Interval | `{n,}` | See the explanation above. |
| Interval | `{n,m}` | See the explanation above. |
| Optional | `?` | It is an alias for `{0,1}` |
| Zero or more | `*` | It is an alias for `{0,}` |
| At least one | `+` | It is an alias for `{1,}` |

In cases when the quantifier should be atomic use:

| Rule | Syntax |
|:----:|:------:|
| Interval | `{n}+` |
| Interval | `{n,}+` |
| Interval | `{n,m}+` |
| Optional | `?+` |
| Zero or more | `*+` |
| At least one | `++` |

### Lazy quantifiers

They will try to match the least times they can before continuing the analysis.

| Rule | Syntax | Meaning |
|:----:|:------:|:--------|
| Interval | `{n}?` | See the explanation above. |
| Interval | `{n,}?` | See the explanation above. |
| Interval | `{n,m}?` | See the explanation above. |
| Optional | `??` | It is an alias for `{0,1}?` |
| Zero or more | `*?` | It is an alias for `{0,}?` |
| At least one | `+?` | It is an alias for `{1,}?` |

In cases when the quantifier should be atomic use:

| Rule | Syntax |
|:----:|:------:|
| Interval | `{n}*` |
| Interval | `{n,}*` |
| Interval | `{n,m}*` |
| Optional | `?*` |
| Zero or more | `**` |
| At least one | `+*` |

## Quantified groups

These lexemes behave in the way that they are able to capture each of their options a specific number of times and also in any position.

Due to that, the quantifier group acts like if it has an inner quantifier that captures at least the addition of all the minimum values of all the options and at most the addition of all the maximum values of all the options, unless these bounds are manually set. In that case, the most restrictive are chosen.  For example:

```lexem
@(option1 | option2 |)          -- min auto, max auto
@({} option1 | option2 |)       -- min auto, max auto
@({x} option1 | option2 |)      -- min set, max auto
@({x,} option1 | option2 |)     -- min set, max auto
@({x,y} option1 | option2 |)    -- min set, max set
@({,y} option1 | option2 |)     -- min auto, max set
```

The search priority is from left to right, so it will try to find first the left-most options.

```lexem
!@(genericQuantifier modifier option1 |quantifier1 option2 |quantifier2)
```

The negation tells the analyzer it is required that the lexeme does _NOT_ match to continue with the normal flow.

The quantified groups are by default greedy, so to change them to lazy (`?`), atomic greedy (`+`) or atomic lazy (`*`) it should be set the modifier at the beginning. For example:

```lexem
@(option1 | option2 |)      -- greedy
@(? option1 | option2 |)    -- lazy
@(+ option1 | option2 |)    -- atomic greedy
@(* option1 | option2 |)    -- atomic lazy
```

Each of the options must be suffixed with (`|`) followed by a quantifier that specifies the number of captures required for that option. If it is omitted the default quantifier is `{1}`.

For example, for `@("x"| "y"|? "z"|{1,2})` its calculated global quantifier would be `{2,4}` and will capture the following patterns ordered by priority from left to right and top to bottom, considering the modifier is greedy:

| Option | Option | Option | Option |
|:------:|:------:|:------:|:------:|
| xyzz   | xyz    | xzzy   | xzz    |
| xzyz   | xzy    | xz     | yxzz   |
| yxz    | yzxz   | yzx    | yzzx   |
| zxyz   | zxy    | zxzy   | zxz    |
| zx     | zyxz   | zyx    | zyzx   |
| zzxy   | zzx    | zzyx   |        |

## Anchors

These lexemes allows to detect key positions inside the input. There are two types, each one with an specific syntax.

### Relative anchors

This type detect a start or end regarding a relative element, for example, a character, a fixed expression, etc.

```lexem
!^(elements)    -- Start of...
!$(elements)    -- End of...
```

The negation tells the analyzer it is required that the lexeme does _NOT_ match to continue with the normal flow.

The allowed elements are:

| Rule | Syntax | Meaning |
|:----:|:------:|:--------|
| Text | `text` | Detects the start or the end of the whole input. |
| Line | `line` | Detects the start or the end of a line, i.e. over the jump-line character (`\n`).
| String | `"characters"` | Detects the start or the end of an specified `String` value. The anchor is affected by the `insensible` and `reverse` properties. Any string literal can be used but not escaped expressions. |
| Block | `itv![characters]` or `uitv![characters]` | Detects the start or the end of an specified character block. The anchor is affected by the `insensible` and `reverse` properties. Any interval literal can be used but not escaped expressions. |

Moreover, there are a few abbreviations due to they are commonly used:

| Rule | Syntax | Meaning |
|:----:|:------:|:--------|
| `^` | `^(text line)` | Start of line. |
| `$` | `$(text line)` | End of line. |
| `^^` | `^(text)` | Start of whole input. |
| `$$` | `$(text)` | Enf of whole input. |
| `!^` | `!^(text line)` | Start of line (negated). |
| `!$` | `!$(text line)` | End of line (negated). |
| `!^^` | `!^(text)` | Start of whole input (negated). |
| `!$$` | `!$(text)` | Enf of whole input (negated). |

### Absolute anchors

This type detect a fixed position over the input.

```lexem
!&(elements)
```

The negation tells the analyzer it is required that the lexeme does _NOT_ match to continue with the normal flow.

The allowed elements are:

| Rule | Syntax | Meaning |
|:----:|:------:|:--------|
| Input start | `from_start[exp]` | Detects the specified position from the beginning of the whole input. |
| Input end | `from_end[exp]` | Detects the specified position from the end of the whole input. |
| Analysis beginning | `analysis_beginning[exp]` | Detects the specified position from the position where the analysis began. |

## Property modifier

This node is really a macro so it can be used in functional code as well. Its functionality consist on change fastly the properties of the current node.

```lexem
set_props![...]
```

It uses the same syntax of the _Property-style object definition_.

> **Note**: it does not overwrite the whole properties object but only those properties that are modified.

## Accesses

These lexemes are very important because they offer the possibility to call other expressions to delegate the capture to them.

```lexem
!expression(arg1: val1, arg2: val2, props: properties)
!expression(arg1: val1, arg2: val2):[properties]
```

The negation tells the analyzer it is required that the lexeme does _NOT_ match to continue with the normal flow.

The two elements of the accesses are:

- **Arguments**: dynamic values passed to the calling expression.
- **Properties**: the properties that are passed to the calling expression. This field (`:[properties]`) is optional.

### Re-parsing

There are situations in which it is necessary to capture a generic syntax and then re-parse it again to analyze in deep its meaning.
To perform this task it is allowed to call another expression after parsing.

```lexem
access -> !expression(arg1: val1, arg2: val2, props: properties)
access -> !expression(arg1: val1, arg2: val2):[properties]
```

The negation tells the analyzer it is required that the access does _NOT_ match to continue with the normal flow.

> **Note**: you can chain any number of accesses but they cannot be set after a filter.

### Filtering

A filter allows to analyze in a higher level the structure of a node and allows to modify it.

```lexem
access -> !filter(arg1: val1, arg2: val2, props: properties)
access -> !filter(arg1: val1, arg2: val2):[properties]
```

The negation tells the analyzer it is required that the filter does _NOT_ match to continue with the normal flow.

The three elements of the accesses are:

- **Arguments**: dynamic values passed to the calling expression.
- **Properties**: the properties that are passed to the called expression. This field (`:[properties]`) is optional.

> **Note**: you can chain any number of filters but always after all accesses.

## Executor (Embed functional code)

This lexemes allow to execute functional code in the middle of a descriptive code, e.g. a pattern.

There are two types:

- **Static**: they just execute the functional code.

    ```lexem
    \(exp1, exp2)
    ```

- **Dynamic**: they execute the functional code using the result of the last expression as condition to start the backtracking.

    ```lexem
    \(? exp1, exp2, condition)
    ```

## Continuation

Allows to continue the current pattern on the next line. Really it is not a lexem but a syntactic-sugar.

```lexem
|> a1 \
a2
```

## Data capturing

It consist of giving a name to a node associating it with a semantic meaning in the semantic tree.

```lexem
name = lexeme
```

It acts as a suffix for any lexeme implying that if the lexeme is captured, its content will be stored inside a variable called `name`.
In case of any lexeme that creates a node (e.g. accesses, capturing groups, etc.), `name` has an object as value with the following structure:

```lexem
{
    content: STRING,    -- The content captured by the lexeme.
    node: NODE,         -- The node generated by the lexeme.
}
```

Moreover, if the lexeme captures once, `name` holds the value but if it captures more, the variable will contain a list of values.

## Semantic re-naming

It consist of giving a new name to a node to improve the semantic meaning of the result tree of nodes.

```lexem
name:lexeme
```

It acts as a prefix for the _access_ and _group_ lexemes that capture a node.