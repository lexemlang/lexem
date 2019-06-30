# Index

- [Index](#Index)
- [Functional expressions](#Functional-expressions)
  - [Indexers](#Indexers)
  - [Accesses](#Accesses)
  - [Function calls](#Function-calls)
  - [Operators](#Operators)
    - [Unitary operators](#Unitary-operators)
    - [Binary operators](#Binary-operators)
    - [Chained binary operators (relational)](#Chained-binary-operators-relational)
    - [Chained binary operators (and, or)](#Chained-binary-operators-and-or)
    - [Chained binary operators (xor)](#Chained-binary-operators-xor)
    - [Assignments](#Assignments)

# Functional expressions

## Indexers

```lasm
# expression (element)
# expression (index)
IDX     # Calls the indexer function of the second last element of the stack with the last element as its index
```

## Accesses

To variables:

```lasm
CTX     # Adds to the stack the current context
# expression (variable name)
ACC     # Adds the value of the property called as the last value of the stack indicates from the second last value of the stack
```

To other objects:

```lasm
# expression (element to index)
# expression (property name)
ACC     # Adds the value of the property called as the last value of the stack indicates from the second last value of the stack
```

## Function calls

```lasm
# expression (function)
LIT:OBJ:NEW     # Adds a new empty object to the stack
# Expression (key)
# Expression (value)
LIT:OBJ:ADD     # Adds the computed value to the object with the specified key and push it back to the stack
...
# Expression (key)
# Expression (value)
LIT:OBJ:ADD
FUN:CALL        # Calls a function changing the module and code, creating a new context, etc.
```

> **Note**: if the first argument has no name, it uses `firstArg`.

## Operators

### Unitary operators

```lasm
# operand
OP:*       # Performs the (*) operation with the last value of the stack
OP:*
...
```

The binary operator instructions available are:

| Name | Description |
|:----:|:------------|
| `OP:NOT` | Logic negation |
| `OP:PLS` | Arithmetic affirmation |
| `OP:NEG` | Arithmetic negation |
| `OP:BTW` | Bit reverser |

### Binary operators

```lasm
# operand 1
# operand 2
OP:*       # Performs the (*) operation with the last 2 values of the stack
# operand 3
OP:*
...
```

The binary operator instructions available are:

| Name | Description |
|:----:|:------------|
| `OP:MUL` | Product |
| `OP:DIV` | Division |
| `OP:DIV:INT` | Integer division |
| `OP:MOD` | Reminder of integer division |
| `OP:ADD` | Addition |
| `OP:SUB` | Subtraction |
| `OP:SFT:R` | Right shift |
| `OP:SFT:L` | Left shift |
| `OP:ROT:R` | Right rotation |
| `OP:ROT:L` | Left rotation |
| `OP:AND` | Logic AND |
| `OP:OR` | Logic OR |
| `OP:XOR` | Logic XOR |

### Chained binary operators (relational)

```lasm
# operand 1
# operand 2
OP:* @end   # Performs the (*) operation with the last value of the stack
...
# operand 3
OP:* @end
DEL
LIT:TRUE
@end:
```

The chained binary operator instructions available are:

| Name | Description |
|:----:|:------------|
| `OP:GT` | Greater than |
| `OP:LT` | Lower than |
| `OP:GET` | Greater or equal than |
| `OP:LET` | Lower or equal than |
| `OP:EQT` | Equal than |
| `OP:NEQT` | Different of |
| `OP:ID` | Identity |
| `OP:NID` | No-identity |

Every of these operators check their condition against the last two values of the stack and if it is `true`, keeps the last value and continues. On the other hand, adds a `false` to the stack and jumps to `@end`.

### Chained binary operators (and, or)

```lasm
# operand 1
OP:CND:* @end     # Performs the (*) operation with the last value of the stack
# operand 2
OP:CND:* @end
...
# operand n
@end:
```

The chained binary operator instructions available are:

| Name | Description |
|:----:|:------------|
| `OP:CND:AND` | Checks if the last value of the stack is `falsy` to keep that value in the stack and jump to `@end`. In other case it removes that value from the stack and continues |
| `OP:CND:OR` | Checks if the last value of the stack is `truthy` to keep that value in the stack and jump to `@end`. In other case it removes that value from the stack and continues |

### Chained binary operators (xor)

```lasm
# operand 1
# operand 2
OP:CND:XOR @end   # Performs the (*) operation with the last value of the stack
...
# operand 3
OP:CND:XOR @end
@end:
```

| Name | Description |
|:----:|:------------|
| `OP:CND:XOR` | If the first operand is `falsy` adds to the stack the second operand. If both are `truthy` adds a `false` to the stack and jumps to `@end`. In the last case adds to the stack the first operand |

### Assignments

Without operator:

```lasm
# left expression
# right expression
OP:ASG      # Assigns the last value of the stack in the previous one
```

With operator:

```lasm
# left expression
CLONE       # Clones the last element of the stack
# right expression
OP:*
OP:ASG      # Assigns the last value of the stack in the previous one
```
