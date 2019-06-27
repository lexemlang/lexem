# Lexem language

> THIS IS A WORK IN PROGRESS, STAY TUNED!!


Lexem is a script language which has the ability to parse textual inputs based on custom grammars. Like [Regular Expressions](https://www.regular-expressions.info/), Lexem allows the developer to define specific sequences of tokens that define the grammar Lexem must follow to parse the inputs.

On one hand, Lexem is a declarative language that allows to define how the input must be parsed but, on the other hand, it is also a pure functional language, i.e. like C or JavaScript, Lexem has functions, object, etc.

Thus, Lexem has implemented in its core a complex backtracking system that allows to reset the execution to any past state, including all functional state, like variable values.

To sum up, Lexem is able to analyze:

- Serialized binary data.
- Context-free grammars, like programming languages.
- Context-sensitive grammars, like natural languages.

To finally return a tree-like document with the result of the analysis, normally `JSON` (but `XML` is also supported).

To perform these jobs, *Lexem* is composed by two sections or cores:

- **Descriptive core**: this section defines how the input text will be captured, e.g. something like "in this position a period `.` must be found followed by an `identifier`".
- **Functional core**: this section is like any other scripting language and allows to control the descriptive section to adapt it depending on the context.

Both are joined in a way that can be used at the same time with no conflicts improving the functionality of Lexem.

## Documentation

To know more about Lexem see one the following sections:

- The [specification](specification/README.md) of Lexem.
- The Lexem's self-defined [grammar](grammar/README.md).
- The [do it yourself](diy/README.md) section to learn how to implement a compiler and/or and interpreter.

## Contributing

If you want to contribute, make an issue request using the most suitable pattern for your request, or mail us through support@lexemlang.org.