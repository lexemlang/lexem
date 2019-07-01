
# Index

- [Index](#Index)
- [Lexemes](#Lexemes)
  - [Groups](#Groups)
  - [Quantifiers](#Quantifiers)
  - [Quantified groups](#Quantified-groups)
  - [Filter](#Filter)
    - [Name](#Name)
    - [Properties](#Properties)
    - [Methods](#Methods)
  - [Additions](#Additions)
    - [Name](#Name-1)
    - [Properties](#Properties-1)
  - [Accesses](#Accesses)
  - [Executor (Embed functional code)](#Executor-Embed-functional-code)
  - [Continuation](#Continuation)
  - [Data-capturing](#Data-capturing)
  - [Semantic re-naming](#Semantic-re-naming)

# Lexemes

The filter lexemes are the minimum descriptive piece of code to describe a filter for a node.

There are two types of lexemes, those that define what content should be capture when the lexeme is executed and those that only change the flow of the analyzer.

## Groups

This lexeme is the same as in expressions. See [Groups](../expressions/lexemes.md#Groups) for more details.

## Quantifiers

This lexeme is the same as in expressions. See [Quantifiers](../expressions/lexemes.md#Quantifiers) for more details.

## Quantified groups

This lexeme is the same as in expressions. See [Quantifiers](../expressions/lexemes.md#Quantified-groups) for more details.

## Filter

These lexemes captures child nodes that match the specified selector.

```lexem
!@( selector )
```

The negation tells the analyzer it is required that the lexeme does _NOT_ match to continue with the normal flow.

The selector is composed by different sections. For example, a fully defined selector is:

```lexem
!@( name .property1 .property2 :method1(...) :method2(...) )
```

### Name

The name section evaluates the name of the node and try to match it using one of the following rules:

```lexem
name            #- the specific name
!name           #- not the specific name
(name, name2)   #- any of these names
!(name, name2)  #- none of these names
```

> **Note**: if this section is omitted, the selector does not filter by the name of the node.

### Properties

On the other hand, to check a property use one of the following rules:

```lexem
.property                    #- the property must exist
.!property                   #- the property must not exist
.property[condition]         #- the property must exist and the condition must match using the 'it' alias
.property[alias: condition]  #- the property must exist and the condition must match using the specified alias
.(prop1, prop2)              #- any of the properties
```

Also, there is a set of reserved property keys:

- `@name`: allows to perform complex checks over the name of the node.
- `@content`: allows to perform complex checks over the content of the node.
- `@start`: allows to perform complex checks over the start of the content.
- `@end`: allows to perform complex checks over the end of the content.
- `@node`: allow to perform complex checks over the node itself.

> **Note**: this section is optional.

### Methods

Finally, the methods provide a way to define complex checks over different elements of the node.

- `:root`: it is the root of the tree i.e. has not a parent.
- `:empty`: the node must not have any child.
- `:child-size(size: condition)`: the number of children of the node must match the condition.
- `:first-child`: the node position inside the child list of its parent must be the first.
- `:last-child`: the node position inside the child list of its parent must be the last.
- `:nth-child(nth: condition)`: the node position inside the child list of its parent must match the condition.
- `:nth-last-child(nth: condition)`: the node position inside the child list of its parent must match the condition.
- `:parent(selector)`:  #- it has a parent and match the selector.
- `:all-children(selector)`: all children of the node must match the selector.
- `:any-child(selector)`: at least one child of the node must match the selector.
- `:qtf-children({min, max}: selector)`: the number of children specified by the quantifier must match the selector.
- `:node(it: condition)`: allow to perform complex checks over the node.

There is also a negated version of each one, just put a `!` between `:` and the name, e.g. `:!root()`

The default name to access the contextual value in all methods is `it`.

> **Note**: this section is optional.

## Additions

Using similar selectors as _Filter_, this node generates a new child node at the current position.

```lexem
+@( selector )
```

The selector is composed by different sections. For example, a fully defined selector is:

```lexem
@( name .property )
```

### Name

Sets the name of the section evaluates the name of the node and try to match it using one of the following rules:

```lexem
*               #- any name
name            #- the specific name
!name           #- not the specific name
(name, name2)   #- any of these names
!(name, name2)  #- none of these names
```

### Properties

On the other hand, to check a property use one of the following rules:

```lexem
.property                    #- the property must exist
.!property                   #- the property must not exist
.property[condition]         #- the property must exist and the condition must match using the 'it' alias
.property[alias: condition]  #- the property must exist and the condition must match using the specified alias
.(prop1, prop2)              #- any of the prperties
```

## Accesses

These nodes allow to call another filter over the specified node.

```lexem
filter/addition -> !filter(arg1: val1, arg2: val2):[properties]
```

The negation tells the analyzer it is required that the access does _NOT_ match to continue with the normal flow.

> **Note**: you can chain any number of filters.

## Executor (Embed functional code)

This lexeme is the same as in expressions. See [Executor](../expressions/lexemes.md#Executor-Embed-functional-code) for more details.

## Continuation

This lexeme is the same as in expressions. See [Continuation](../expressions/lexemes.md#Continuation) for more details.

## Data-capturing

This lexeme is the same as in expressions. See [Data capturing](../expressions/lexemes.md#Data-capturing) for more details.

## Semantic re-naming

This lexeme is the same as in expressions. See [Semantic re-naming](../expressions/lexemes.md#Semantic-re-naming) for more details.