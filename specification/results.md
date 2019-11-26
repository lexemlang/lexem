# Table of contents

- [Table of contents](#table-of-contents)
- [Lexem results](#lexem-results)

# Lexem results

In every execution of an analysis, a node is created as result. That means the analysis always returns a built-in node that contains your custom nodes as children.

For example, if you parse a JSON file, the result could be:

```plain
- root
  - JsonObject
    - ...
```

While if you parse a Markdown file, it could be:

```plain
- root
  - header
  - table of contents
  - text
  - code
    - JsonObject
```
