# Index

- [Index](#Index)
- [Literals' translation to instructions](#Literals-translation-to-instructions)
  - [Null type](#Null-type)
  - [Logic type](#Logic-type)
  - [Integer type](#Integer-type)
  - [Float type](#Float-type)
  - [String type](#String-type)
    - [With dynamic elements](#With-dynamic-elements)
  - [Bitlist type](#Bitlist-type)
    - [With dynamic elements](#With-dynamic-elements-1)
  - [Interval type](#Interval-type)
    - [Subintervals](#Subintervals)
  - [List type](#List-type)
  - [Set type](#Set-type)
  - [Object type](#Object-type)
  - [Map type](#Map-type)
  - [Function type](#Function-type)
  - [Expression type](#Expression-type)

# Literals' translation to instructions

## Null type

```lasm
LIT:NULL    # Adds a null value to the stack
```

## Logic type

```lasm
LIT:TRUE    # Adds a true value to the stack
LIT:FALSE   # Adds a false value to the stack
```

## Integer type

```lasm
LIT:INT integer     # Adds the inline integer value to the stack
```

- `integer`: 64 bit inline integer

## Float type

```lasm
LIT:FLT float       # Adds the inline float value to the stack
```

- `float`: 64 bit inline float

## String type

```lasm
LIT:STR #string     # Adds the specified string value to the stack
```

- `string`: 32 bit inline integer that refers to the index of a string constant.

### With dynamic elements

```lasm
LIT:STR #string     # This should be a constant string or an empty one
# Expression
OP:ADD
...
# Expression
OP:ADD
```

> **Note**: "a{x}c" = "a" + x + "c", "{x}c" = "" + x + "c"

## Bitlist type

```lasm
LIT:BLST #bitlist   # Adds the specified bitlist value to the stack
```

- `bitlist`: 32 bit inline integer that refers to the index of a bitlist constant.

### With dynamic elements

```lasm
LIT:BLST #string    # This should be a constant bitlist or an empty one
# Expression
OP:ADD
...
# Expression
OP:ADD
```

> **Note**: 0b"101{x}1010" = "101" + x + "1010", "{x}11" = "" + x + "11"

## Interval type

```lasm
LIT:ITV:NEW     # Adds a new empty interval to the stack
LIT:UITV:NEW    # Adds a new empty unicode interval to the stack
# Expression (from)
# Expression (to)
LIT:ITV:RNG     # Adds the computed range to the interval and push the interval back to the stack
...
# Expression (from)
# Expression (to)
LIT:ITV:RNG
```

### Subintervals

```lasm
# main interval
# subinterval
LIT:ITV:NOT     # Reverts the (unicode) interval
LIT:ITV:ADD     # Creates one interval with the content of both
LIT:ITV:SUB     # Removes from the main interval the content of the subinterval
LIT:ITV:AND     # Creates one interval with the common content of both
LIT:ITV:XOR     # Creates one interval with the not-common content of both
```

## List type

```lasm
LIT:LST:NEW     # Adds a new empty list to the stack
LIT:LST:SNEW    # Adds a new empty constant list to the stack
# Expression
LIT:LST:ADD     # Adds the computed value to the list and push it back to the stack
...
# Expression
LIT:LST:ADD
```

## Set type

```lasm
LIT:SET:NEW     # Adds a new empty set to the stack
LIT:SET:SNEW    # Adds a new empty constant set to the stack
# Expression
LIT:SET:ADD     # Adds the computed value to the set and push it back to the stack
...
# Expression
LIT:SET:ADD
```

## Object type

```lasm
LIT:OBJ:NEW     # Adds a new empty object to the stack
LIT:OBJ:SNEW    # Adds a new empty constant object to the stack
# Expression (key)
# Expression (value)
LIT:OBJ:ADD     # Adds the computed value to the object with the specified key and push it back to the stack
...
# Expression (key)
# Expression (value)
LIT:OBJ:ADD
```

## Map type

```lasm
LIT:MAP:NEW     # Adds a new empty map to the stack
LIT:MAP:SNEW    # Adds a new empty constant map to the stack
# Expression (key)
# Expression (value)
LIT:MAP:ADD     # Adds the computed value to the map with the specified key and push it back to the stack
...
# Expression (key)
# Expression (value)
LIT:MAP:ADD
```

## Function type

```lasm
LIT:FUN #function     # Adds the specified function to the stack
```

## Expression type

```lasm
LIT:EXP #expression   # Adds the specified expression to the stack
```