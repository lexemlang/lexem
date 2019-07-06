
# Index

- [Index](#Index)
- [Instruction set](#Instruction-set)
  - [Simple](#Simple)
  - [With inline value](#With-inline-value)

# Instruction set

> **Note**: the `S0` is the last element in the stack while `S1` is the previous one.

## Simple

| Name | Description |
|:----:|:------------|
| `ERR` | Throws an execution error due to a invalid state |
| `DEL` | Removes `S0` |
| `CLONE` | Clones `S0` |
| `CTX` | Adds the current context to the stack |
| `LIT:NULL` | Adds a `null` value to the stack |
| `LIT:TRUE` | Adds a `true` value to the stack |
| `LIT:FALSE` | Adds a `false` value to the stack |
| `LIT:ITV:NEW` | Adds a new empty interval to the stack |
| `LIT:ITV:RNG` | Adds the computed range to the interval and push the interval back to the stack |
| `LIT:ITV:NOT` | Reverts the interval in `S0` |
| `LIT:ITV:U:NOT` | Reverts the unicode interval in `S0` |
| `LIT:ITV:ADD` | Creates one interval with the content of `S0` and `S1` |
| `LIT:ITV:SUB` | Removes the content of the sub-interval (`S0`) from the main interval (`S1`) |
| `LIT:ITV:AND` | Creates one interval with the common content of `S0` and `S1` |
| `LIT:ITV:XOR` | Creates one interval with the not-common content of `S0` and `S1` |
| `LIT:LST:NEW` | Adds a new empty list to the stack |
| `LIT:LST:ADD` | Adds the computed value (`S0`) to the list (`S1`) |
| `LIT:SET:NEW` | Adds a new empty set to the stack |
| `LIT:SET:ADD` | Adds the computed value (`S0`) to the set (`S1`) |
| `LIT:OBJ:NEW` | Adds a new empty object to the stack |
| `LIT:OBJ:ADD` | Adds the computed value (`S0`) to the object (`S1`) |
| `LIT:MAP:NEW` | Adds a new empty map to the stack |
| `LIT:MAP:ADD` | Adds the computed value (`S0`) to the map (`S1`) |
| `IDX` | Calls the indexer function over `S1` with `S0` as its index |
| `ACC` | Adds the value of the property of `S1` indicated by `S0` into the stack |
| `FUN:CALL` | Calls a function changing the module and code, creating a new context, etc. |
| `OP:NOT` | Logic negation over `S0` |
| `OP:NEG` | Arithmetic negation over `S0` |
| `OP:BTW` | Bit reverser over `S0` |
| `OP:MUL` | Product over `S0` and `S1` |
| `OP:DIV` | Division over `S0` and `S1` |
| `OP:DIV:INT` | Integer division over `S0` and `S1` |
| `OP:MOD` | Reminder of integer division over `S0` and `S1` |
| `OP:ADD` | Addition over `S0` and `S1` |
| `OP:SUB` | Subtraction over `S0` and `S1` |
| `OP:SFT:R` | Right shift over `S0` and `S1` |
| `OP:SFT:L` | Left shift over `S0` and `S1` |
| `OP:ROT:R` | Right rotation over `S0` and `S1` |
| `OP:ROT:L` | Left rotation over `S0` and `S1` |
| `OP:AND` | Logic AND over `S0` and `S1` |
| `OP:OR` | Logic OR over `S0` and `S1` |
| `OP:XOR` | Logic XOR over `S0` and `S1` |
| `OP:ASG` | Assigns `S0` to `S1` |
| `OP:MK:CNST` | Make `S0` constant |

## With inline value

| Name | Value | Description |
|:----:|:-----:|:------------|
| `JP` | `@end` | Unconditional jump |
| `JPT` | `@end` | Conditional jump. `S0` must be `truthy` |
| `JPF` | `@end` | Conditional jump. `S0` must be `falsy` |
| `LIT:INT` | `integer` | Adds the inline `Integer` value to the stack |
| `LIT:FLT` | `float` | Adds the inline `Float` value to the stack |
| `LIT:STR` | `#string` | Adds the specified `String` value to the stack |
| `LIT:ITV` | `#itv` | Adds the specified `Interval` value to the stack |
| `LIT:BLST` | `#bitlist` | Adds the specified `Bitlist` value to the stack |
| `LIT:FUN` | `#function` | Adds the specified `Function` to the stack |
| `LIT:EXP` | `#expression` | Adds the specified `Expression` to the stack |
| `OP:GT` | `@end` | Greater than comparator over `S0` and `S1`  |
| `OP:LT` | `@end` | Lower than over `S0` and `S1` |
| `OP:GET` | `@end` | Greater or equal than over `S0` and `S1` |
| `OP:LET` | `@end` | Lower or equal than over `S0` and `S1` |
| `OP:EQT` | `@end` | Equal than over `S0` and `S1` |
| `OP:NEQT` | `@end` | Different of over `S0` and `S1` |
| `OP:ID` | `@end` | Identity over `S0` and `S1` |
| `OP:NID` | `@end` | No-identity over `S0` and `S1` |
| `OP:CND:AND` | `@end` | Checks if `S0` is `falsy` to keep it in the stack and jump to `@end`. In other case it removes `S0` and continues |
| `OP:CND:OR` | `@end` | Checks if `S0` is `truthy` to keep it in the stack and jump to `@end`. In other case it removes `S0` and continues |
| `OP:CND:XOR` | `@end` | If `S1` is `falsy` removes it from the stack, keeping `S0`. If `S0` is `falsy` removes it from the stack, keeping `S1`. Finally, if both are `truthy` adds a `false` to the stack and jumps to `@end`.

Every inline value, including the references are 64-bit length and they are written in big endian.
