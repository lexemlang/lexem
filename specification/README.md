# Specifications

- [Comments](./comments.md)
- [Modules](./modules.md)

### Functional core

- [Data types](./functional/types.md)
- [Statements](./functional/statements.md)
- [Expressions](./functional/expressions.md)
- [Macros](./functional/macros.md)

### Descriptive core

- [Expressions](./descriptive/expressions.md)
- [Lexems](./descriptive/lexemes.md)
- [Statements](./descriptive/statements.md)

## LASM

The _Lexem assembler_, abbreviated as *LASM* is the intermediate representation of the lexem code used to accelerate the execution and to be able to perform the backtracking correctly.

- List of available [Instructions](./lasm/instructions.md)
- How to [serialize](lasm/file_serialization.md) a file in LASM

The following documents show how to translate all Lexem's elements into LASM:

- [Literals](./lasm/translation/literals.md)
- [Functional expressions](./lasm/translation/functional_expressions.md)
