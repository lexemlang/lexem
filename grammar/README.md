# Grammar

All Lexem files (`.lxm`) under this folder shows the grammar of the Lexem language written in itself.

### Index

#### Commons

- [Lexem](lexem.lxm): entry point of the grammar with the syntax to parse a whole Lexem file (`.lxm`).
- [Commons](commons.lxm): all common elements of the grammar, like comments, whitespaces, identifiers, etc.
- [Literals](literals.lxm): a file to gather all Lexem's literals, also with the grammar of `Null` and `Logic` literals.
  - [Number](literals/number.lxm): the grammar for `Number` literals.
  - [String](literals/string.lxm): the grammar for `String` literals.
  - [Bitlist](literals/bitlists.lxm): the grammar for `Bitlist` literals.
  - [Interval](literals/intervals.lxm): the grammar for `Interval` literals.
  - [List](literals/list.lxm): the grammar for `List` literals.
  - [Set](literals/set.lxm): the grammar for `Set` literals.
  - [Object](literals/objects.lxm): the grammar for `Object` literals.
  - [Map](literals/maps.lxm): the grammar for `Map` literals.
  - [Function](literals/functions.lxm): the grammar for `Function` literals.

#### Functional core

- [Expression](functional/expressions.lxm): the grammar for a complex functional expression.
- [Statements](functional/statements.lxm): a file to gather all Lexem's functional statements, also with the grammar of some statements.
  - [Conditionals](functional/statements/conditionals.lxm): the grammar for the functional conditional statements.
  - [Selective](functional/statements/selective.lxm): the grammar for the functional selective statement.
  - [Variable declaration](functional/statements/conditionals.lxm): the grammar for the variable declaration statements.
  - [Loops](functional/statements/loops.lxm): the grammar for the functional loop statements.
  - [Controls statements](functional/statements/controls.lxm): the grammar for the control statements.

#### Descriptive core

- [Patterns](descriptive/patterns.lxm): a file to gather all Lexem's descriptive lexemes, also with the grammar for a descriptive pattern.
- [Statements](descriptive/statements.lxm): a file to gather all Lexem's descriptive statements, also with the grammar of some statements.
  - [Conditionals](descriptive/statements/conditionals.lxm): the grammar for the descriptive conditional statements.
  - [Selective](descriptive/statements/selective.lxm): the grammar for the descriptive selective statement.
  - [Loops](descriptive/statements/loops.lxm): the grammar for the descriptive loop statements.
- Lexemes:
  - [Text](descriptive/lexemes/texts.lxm): the grammar for the text lexeme.
  - [Binary_pattern](descriptive/lexemes/binary_patterns.lxm): the grammar for the binary pattern lexeme.
  - [Block](descriptive/lexemes/blocks.lxm): the grammar for the blocks lexemes.
  - [Group](descriptive/lexemes/groups.lxm): the grammar for the group lexeme.
  - [Quantified_group](descriptive/lexemes/quantified_groups.lxm): the grammar for the quantified group lexeme.
  - [Access](descriptive/lexemes/accesses.lxm): the grammar for the access lexeme.
  - [Anchor](descriptive/lexemes/anchors.lxm): the grammar for the anchor lexeme.
  - [Executer](descriptive/lexemes/executers.lxm): the grammar for the executer lexeme.
  - [Quantifiers](descriptive/lexemes/quantifiers.lxm): the grammar for the quantifier lexeme.
