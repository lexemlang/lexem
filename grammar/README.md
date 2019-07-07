# Grammar

All Lexem files (`.lxm`) under this folder shows the grammar of the Lexem language written in itself.

### Index

#### Commons

- [Lexem](lexem.lxm): entry point of the grammar with the syntax to parse a whole Lexem file (`.lxm`).
- [Commons](commons.lxm): all common elements of the grammar, like comments, whitespaces, identifiers, etc.
- [Literals](literals.lxm): a file to gather all Lexem's literals, also with the grammar of `Nil` and `Logic` literals.
    - [Number](literals/number.lxm): the grammar for `Number` literals.
    - [String](literals/string.lxm): the grammar for `String` literals.
    - [Bitlist](literals/bitlist.lxm): the grammar for `Bitlist` literals.
    - [Interval](literals/interval.lxm): the grammar for `Interval` literals.
    - [List](literals/list.lxm): the grammar for `List` literals.
    - [Set](literals/set.lxm): the grammar for `Set` literals.
    - [Object](literals/object.lxm): the grammar for `Object` literals.
    - [Map](literals/maps.lxm): the grammar for `Map` literals.
    - [Function](literals/function.lxm): the grammar for `Function` literals.

#### Functional core

- [Expression](functional/expressions.lxm): the grammar for a complex functional expression.
- [Statements](functional/statements.lxm): a file to gather all Lexem's functional statements, also with the grammar of some statements.
    - [Variable declaration](functional/statements/conditionals.lxm): the grammar for the variable declaration statements.
    - [Conditionals](functional/statements/conditionals.lxm): the grammar for the functional conditional statements.
    - [Selective](functional/statements/selective.lxm): the grammar for the functional selective statement.
    - [Loops](functional/statements/loops.lxm): the grammar for the functional loop statements.
    - [Controls statements](functional/statements/controls.lxm): the grammar for the control statements.

#### Descriptive core

- [Statements](descriptive/statements.lxm): a file to gather all Lexem's descriptive statements, also with the grammar of some statements.
    - [Loops](descriptive/statements/loops.lxm): the grammar for the descriptive loop statements.
- Expressions:
    - [Patterns](descriptive/expressions/patterns.lxm): a file to gather all Lexem's descriptive lexemes, also with the grammar for a descriptive pattern.
    - Lexemes:
        - [Text](descriptive/expressions/lexemes/text.lxm): the grammar for the text lexeme.
        - [Binary_pattern](descriptive/expressions/lexemes/binary_sequence.lxm): the grammar for the binary pattern lexeme.
        - [Block](descriptive/expressions/lexemes/block.lxm): the grammar for the blocks lexemes.
        - [Group](descriptive/expressions/lexemes/group.lxm): the grammar for the group lexeme.
        - [Quantified_group](descriptive/expressions/lexemes/quantified_group.lxm): the grammar for the quantified group lexeme.
        - [Access](descriptive/expressions/lexemes/access.lxm): the grammar for the access lexeme.
        - [Anchor](descriptive/expressions/lexemes/anchor.lxm): the grammar for the anchor lexeme.
        - [Executor](descriptive/expressions/lexemes/executor.lxm): the grammar for the executor lexeme.
        - [Quantifiers](descriptive/expressions/lexemes/quantifier.lxm): the grammar for the quantifier lexeme.
        - [Continuation](descriptive/expressions/lexemes/continuation.lxm): the grammar for the continuation lexeme.
- Filters:
    - [Patterns](descriptive/filters/patterns.lxm): a file to gather all Lexem's filter lexemes, also with the grammar for a descriptive pattern.
    - Lexemes:
        - [Filter](descriptive/filters/lexemes/filter.lxm): the grammar for the filter lexeme.
        - [Addition](descriptive/filters/lexemes/addition.lxm): the grammar for the addition lexeme.
