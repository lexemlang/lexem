# Lexem language

> THIS IS A WORK IN PROGRESS, STAY TUNED!!

*Lexem* is a programming language meant to analyze complex grammar structures. It is inspired by regular expressions and JavaScript, each for one the Lexem's cores. So it is able to analyze:

- Serialized binary data.
- Context-free grammars, like programming languages.
- Context-sensitive grammars, like natural languages.

To finally return a tree-like document with the result of the analysis, normally `JSON` but `XML` is also supported.

To perform these jobs, *Lexem* is composed by two sections or cores:

- **Descriptive core**: this section defines how the input text will be captured, e.g. something like "in this position a period `.` must be found followed by an `identifier`".
- **Functional core**: this section is like any other scripting language and allows to control the descriptive section to adapt it depending on the context.

Both are joined in a way that can be used at the same time with no conflicts improving the functionality of Lexem.

## Documentation

See one the following sections:

- The [specification](./specification/README.md) of Lexem.
- The self-defined [grammar](./grammar/README.md) of Lexem.

## Contributing

If you want to contribute, make an issue request using the most suitable pattern for your request, or mail us through support@lexemlang.org.