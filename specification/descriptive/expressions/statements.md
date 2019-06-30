
# Index

- [Index](#Index)
- [Descriptive statements](#Descriptive-statements)
  - [Quantified loop](#Quantified-loop)
  - [`onback` block](#onback-block)

# Descriptive statements

They are the same of functional code but accepting descriptive code inside their bodies and plus the following additions:

## Quantified loop

Used like the iterator loops but using a quantifier to delimit the repetitions.

```lexem
for quantifier {'tag body}

repeat name for quantifier {'tag body}
```

Using the *indexer* pattern (`repeat name`) each iteration of the loop increase the variable by one.

## `onback` block

The `onback` block allows to execute a piece of functional code when the backtracking comes back through it.

```lexem
|> "abc"

onback {'tag
    log.info("Message")
}

|> "def"
```

Info message is shown only if `"abc"` has matched and `"def"` not. When it is reached during backtracking, all its functional code is executed normally but the backtracking continues.

> **Note**: if you have made changes to repair the flow and you want to continue normally, use the `exit` control flow statement over the `onback` block.