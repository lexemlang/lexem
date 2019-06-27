# Grammar

All Lexem files (`.lxm`) under this folder shows the grammar of the Lexem language written in itself.

## Table of contents

### Commons

- [lexem](lexem.lxm): entry point of the grammar with the syntax to parse a whole Lexem file (`.lxm`).
- [generics](generics.lxm): all common elements of the grammar, like comments, whitespaces, identifiers, etc.
- [literals](literals.lxm): a file to gather all Lexem's literals, also with the grammar of `Null` and `Logic` literals.
  - [numbers](literals/numbers.lxm): the grammar for `Number` literals.
  - [strings](literals/strings.lxm): the grammar for `String` literals.
  - [bitlists](literals/bitlists.lxm): the grammar for `Bitlist` literals.
  - [intervals](literals/intervals.lxm): the grammar for `Interval` literals.
  - [lists](literals/lists.lxm): the grammar for `List` literals.
  - [sets](literals/sets.lxm): the grammar for `Set` literals.
  - [objects](literals/objects.lxm): the grammar for `Object` literals.
  - [maps](literals/maps.lxm): the grammar for `Map` literals.
  - [functions](literals/functions.lxm): the grammar for `Function` literals.
  - [expressions](literals/expressions.lxm): the grammar for `Expression` literals.

### Functional core

- [expressions](functional/expressions.lxm): the grammar for a complex functional expression.
- [statements](functional/statements.lxm): a file to gather all Lexem's functional statements, also with the grammar of some statements.
  - [conditionals](functional/statements/conditionals.lxm): the grammar for the functional conditional statements.
  - [selective](functional/statements/selective.lxm): the grammar for the functional selective statement.
  - [variable declaration](functional/statements/conditionals.lxm): the grammar for the variable declaration statements.
  - [loops](functional/statements/loops.lxm): the grammar for the functional loop statements.
  - [controls](functional/statements/controls.lxm): the grammar for the control statements.

### Descriptive core

- [patterns](descriptive/patterns.lxm): a file to gather all Lexem's descriptive lexemes, also with the grammar for a descriptive pattern.
- [statements](descriptive/statements.lxm): a file to gather all Lexem's descriptive statements, also with the grammar of some statements.
  - [conditionals](descriptive/statements/conditionals.lxm): the grammar for the descriptive conditional statements.
  - [selective](descriptive/statements/selective.lxm): the grammar for the descriptive selective statement.
  - [loops](descriptive/statements/loops.lxm): the grammar for the descriptive loop statements.
- Lexemes:
  - [texts](descriptive/lexemes/texts.lxm): the grammar for the text lexeme.
  - [binary_patterns](descriptive/lexemes/binary_patterns.lxm): the grammar for the binary pattern lexeme.
  - [blocks](descriptive/lexemes/blocks.lxm): the grammar for the blocks lexemes.
  - [groups](descriptive/lexemes/groups.lxm): the grammar for the group lexeme.
  - [quantified_groups](descriptive/lexemes/quantified_groups.lxm): the grammar for the quantified group lexeme.
  - [accesses](descriptive/lexemes/accesses.lxm): the grammar for the access lexeme.
  - [anchors](descriptive/lexemes/anchors.lxm): the grammar for the anchor lexeme.
  - [executers](descriptive/lexemes/executers.lxm): the grammar for the executer lexeme.
  - [quantifiers](descriptive/lexemes/quantifiers.lxm): the grammar for the quantifier lexeme.
