# Specifications

- [Comments](comments.md)
- [Modules](modules.md)
- [Macros](macros.md)

### Functional core

- [Data types](functional/types.md)
- [Statements](functional/statements.md)
- [Expressions](functional/expressions.md)

### Descriptive core

- [Expressions](descriptive/expressions.md)
    - [Lexems](descriptive/expressions/lexemes.md)
    - [Statements](descriptive/expressions/statements.md)

- [Filters](descriptive/filters.md)
    - [Lexems](descriptive/filters/lexemes.md)
    - [Statements](descriptive/filters/statements.md)

## lasm

The _Lexem assembler_, abbreviated as _lasm_ is the intermediate representation of the lexem code used to accelerate the execution and to perform the backtracking correctly.

It is defined as stack-based system, so it is composed by a set of instructions that emulate certain functionality of a processor but it also has complex instructions.

- [Instruction set](lasm/instructions.md)
