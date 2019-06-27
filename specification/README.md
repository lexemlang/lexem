# Specifications

- [Comments](comments.md)
- [Modules](modules.md)

### Functional core

- [Data types](functional/types.md)
- [Statements](functional/statements.md)
- [Expressions](functional/expressions.md)
- [Macros](functional/macros.md)

### Descriptive core

- [Expressions](descriptive/expressions.md)
- [Lexems](descriptive/lexemes.md)
- [Statements](descriptive/statements.md)

## lasm

The _Lexem assembler_, abbreviated as *lasm* is the intermediate representation of the lexem code used to accelerate the execution and to perform the backtracking correctly.

It is defined as stack-based system, so it is composed by a set of instructions that emulate certain functionality of a processor but it also has complex instructions.

- [Instruction set](lasm/instructions.md)
