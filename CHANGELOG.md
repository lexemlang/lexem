# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/)
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [0.2.0] - 2019-08-11

### Add

- Backtracking system specification.
- Parenthesized expression.
- Rest element in parameters.

### Change

- The `null` keyword now is now `nil`.
- The `end` loop clause is now `last`.
- Iterator loops now use only destructuring.
- Move the explanation of the `return` statement.
- Destructuring definition.
- Escape grammar.
- Escaped expression bounds.
- Spread element in arguments.
- Variable declaration.
- Selective statement.

### Improve

- Garbage collector definition for DIY section.
- Object literal definition.
- Simplify the conditional definition.
- Remove useless code.
- Selective statement grammar.
- Statement declarations and macros grammar.
- onBack definition.

### Fix

- Bad documentation references in TOCs.
- False literal grammar.
- Capturing of access expression.
- Escape and normal interval element definitions.
- Analysis order in functional expressions.
- Identifier terminations to not collide with macros.

### Remove

- It is never required to compile the code to the intermediate representation called `lasm`.

## [0.1.1] - 2019-07-04

### Add

- Semantic re-naming lexeme.
- Continuation lexeme.
- Filter statement.
- Filter lexeme of Filters.
- Addition lexeme of Filters.
- No Unicode escapes.
- Filter type.
- Constant simplifications for objects.
- Github support in module imports.
- Imports from project root.

### Change

- The backtrack property of expressions now has its default value to `false`.
- Expressions and filters can omit the parenthesis.
- The block syntax `onback` has changed to `onBack`.
- The inline comment syntax `#-` has changed to `--`.
- The multiline comment syntax (`#+`, `+#`) has changed to (`#-`, `-#`).
- The `backtrack!` macro now can send an object to be caught by an `onBack` block.
- The `file_content!` macro now includes all the content of the current file.

### Improve

- Module imports documentation.
- Variable destructuring.

### Remove

- Support for anonymous expressions and filters.
- The `pattern!` macro.

### :bug: Bug fix

- The addition lexeme of Filters had an incorrect documentation.
- The macros were not being called in the patterns.
- The literals and macros were not being called like an access.

## [0.1.0] - 2019-06-27

### Add

- **Files**: [license](LICENSE), [changelog](#changelog) and main [readme](README.md).
- Initial specification of Lexem and lasm.
- Initial grammar of Lexem.
- Initial do-it-yourself section to explain the compilation and interpretation.
