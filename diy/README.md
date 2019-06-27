# Do it yourself

This series of documents explain how to implement a compiler for the Lexem language and also how to implement just only a valid interpreter for _lasm_.

## Lexem compiler

A Lexem compiler generates lasm code as a result. You can implement your own Lexem compiler if you need to embed it in your project, but if you have internet connection or you want to manually compile, you can use the REPL and API of [https://lexemlang.org]().

If you still require to embed a compiler, you can implement your own Lexem compiler following these steps:

1. The very first thing you have to do is create a parser for Lexem to get the Lexem's code in a way you can understand, like an [AST](https://en.wikipedia.org/wiki/Abstract_syntax_tree) tree.
2. Next, you must translate each Lexem element to lasm using the guide we provide to be an official implementation of Lexem.
3. After that you must serialize the generated lasm into a common binary format (normally stored in `.lasm` files) to be compatible with all other interpreters.
4. Finally, if your project is public, tell us about your project through Github or our mail support@lexemlang.org tto include it in our official list of implementations :).

> **Note**: to be recognized as a valid Lexem compiler you must pass a set of tests (see `WIP`).

### Parser

The implementation of the parser is not opinionated, create it in whatever way you want but bear in mind to follow the official [grammar](.grammar/README.md) to parse exactly the same code.

### Lexem to lasm translation

To know how to translate each element of Lexem to the instruction set os lasm see the following sections:

- [Literals](lasm/translation/literals.md)
- [Functional expressions](lasm/translation/functional_expressions.md)

### Serialize into lasm file

Instructions to serialize a Lexem project into a binary format to save it into a `.lasm` file.

- [File serialization](lasm/file_serialization.md)

## lasm interpreter

A lasm interpreter reads a `.lasm` file and interprets it to analyze the provided input.

To build a valid interpreter follow this guide:

1. Review the instructions functionality and implement it following the official guide to achieve the same behaviour.
2. Implement a memory system including a garbage collector to manage the internal data of Lexem.
3. Implement and manage the backtracking system.
4. The next step is to deserialize the input `.lasm` file.
5. Execute the analysis.
6. Return the results as a tree structure of nodes. Normally `json`, `xml` or any other format you want.
7. If your implementation is public, tell us about your project through Github or our mail support@lexemlang.org tto include it in our official list of implementations :).

> **Note**: to be recognized as a valid lasm interpreter you must pass a set of tests (see `WIP`) and implement the `json` output format.

### Instructions functionality

`WIP`

### Memory definition

`WIP`

### Garbage collector definition

`WIP`

### Backtracking system

`WIP`

### Deserialize from a lasm file

Instructions to serialize a lasm file into a binary format to save it into a `.lasm` file.

- `WIP` File deserialization.

### Analysis

Some parts of the interpreter are not opinionated to let developers to research and invent new ways to do them in order to improve Angmar itself and other implementations.

Because of that, the analysis itself is not ruled and you can implement it the way you want.

