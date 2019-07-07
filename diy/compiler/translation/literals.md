# Index

- [Index](#Index)
- [LASM translation: Literals](#LASM-translation-Literals)
  - [Null type](#Null-type)
  - [Logic type](#Logic-type)
  - [Integer type](#Integer-type)
  - [Float type](#Float-type)
  - [String type](#String-type)
    - [With dynamic elements](#With-dynamic-elements)
  - [Interval type](#Interval-type)
    - [Referenced](#Referenced)
    - [Created](#Created)
    - [Sub-intervals](#Sub-intervals)
  - [Bitlist type](#Bitlist-type)
    - [With dynamic elements](#With-dynamic-elements-1)
  - [List type](#List-type)
  - [Set type](#Set-type)
  - [Object type](#Object-type)
  - [Map type](#Map-type)
  - [Function type](#Function-type)
  - [Expression type](#Expression-type)
  - [Filter type](#Filter-type)

# LASM translation: Literals

## Null type

```lasm 
LIT:NIL     # Adds a null value to the stack
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

- `integer`: 64 bit inline integer in big endian.

## Float type

```lasm
LIT:FLT float       # Adds the inline float value to the stack
```

- `float`: 64 bit inline float in big endian.

## String type

```lasm
LIT:STR #string     # Adds the specified string value to the stack
```

- `string`: 64 bit inline integer that refers to the index of a string constant.

### With dynamic elements

```lasm
LIT:STR #string     # This should be a constant string or an empty one (position 0)
# Expression
OP:ADD
...
# Expression
OP:ADD
```

> **Note**: "a{x}c" = "a" + x + "c", "{x}c" = "" + x + "c"

## Interval type

An interval can be created dynamically or be referenced if it was created during compilation.

### Referenced

```lasm
LIT:ITV #itv        # Adds the specified interval value to the stack
```

- `itv`: 64 bit inline integer that refers to the index of an interval constant.

### Created

```lasm
LIT:ITV:NEW     # Adds a new empty interval to the stack
# Expression (from)
# Expression (to)
LIT:ITV:RNG     # Adds the computed range to the interval and push the interval back to the stack
...
# Expression (from)
# Expression (to)
LIT:ITV:RNG
```

### Sub-intervals

```lasm
# main interval
# subinterval
LIT:ITV:NOT     # Reverts the interval
LIT:ITV:U:NOT   # Reverts the unicode interval
LIT:ITV:ADD     # Creates one interval with the content of both
LIT:ITV:SUB     # Removes from the main interval the content of the subinterval
LIT:ITV:AND     # Creates one interval with the common content of both
LIT:ITV:XOR     # Creates one interval with the not-common content of both
```

## Bitlist type

```lasm
LIT:BLST #bitlist   # Adds the specified bitlist value to the stack
```

- `bitlist`: 64 bit inline integer that refers to the index of a bitlist constant.

### With dynamic elements

```lasm
LIT:BLST #string    # This should be a constant bitlist or an empty one (position 0)
# Expression
OP:ADD
...
# Expression
OP:ADD
```

> **Note**: 0b"101{x}1010" = "101" + x + "1010", "{x}11" = "" + x + "11"

## List type

```lasm
LIT:LST:NEW     # Adds a new empty list to the stack
# Expression
LIT:LST:ADD     # Adds the computed value to the list and push it back to the stack
...
# Expression
LIT:LST:ADD
OP:MK:CNST      # Make the list constant
```

## Set type

```lasm
LIT:SET:NEW     # Adds a new empty set to the stack
# Expression
LIT:SET:ADD     # Adds the computed value to the set and push it back to the stack
...
# Expression
LIT:SET:ADD
OP:MK:CNST      # Make the set constant
```

## Object type

```lasm
LIT:OBJ:NEW     # Adds a new empty object to the stack
# Expression (key)
# Expression (value)
LIT:OBJ:ADD     # Adds the computed value to the object with the specified key and push it back to the stack
...
# Expression (key)
# Expression (value)
LIT:OBJ:ADD
OP:MK:CNST      # Make the object constant
```

## Map type

```lasm
LIT:MAP:NEW     # Adds a new empty map to the stack
# Expression (key)
# Expression (value)
LIT:MAP:ADD     # Adds the computed value to the map with the specified key and push it back to the stack
...
# Expression (key)
# Expression (value)
LIT:MAP:ADD
OP:MK:CNST      # Make the map constant
```

## Function type

```lasm
LIT:FUN #function     # Adds the specified function to the stack
```

## Expression type

```lasm
LIT:EXP #expression   # Adds the specified expression to the stack
```

## Filter type

```lasm
LIT:EXP #expression   # Adds the specified filter to the stack
```