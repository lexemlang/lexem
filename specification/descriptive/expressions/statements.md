
# Index

- [Index](#index)
- [Descriptive statements](#descriptive-statements)
  - [Quantified loop](#quantified-loop)
  - [`onBack` block](#onback-block)
      - [Abbreviation](#abbreviation)

# Descriptive statements

They are the same of functional code but accepting descriptive code inside their bodies and plus the following additions:

## Quantified loop

Used like the iterator loops but using a quantifier to delimit the repetitions.

```lexem
for quantifier {'tag body}

repeat name for quantifier {'tag body}
```

Using the _indexer_ pattern (`repeat name`) each iteration of the loop increase the variable by one.

## `onBack` block

The `onBack` block allows to execute a piece of functional code when the backtracking comes back through it.

```lexem
|> "abc"

onBack {'tag
    log.info("Message")
}

|> "def"
```

Info message is shown only if `"abc"` has matched and `"def"` not. When it is reached during backtracking, all its functional code is executed normally but the backtracking continues.

### Recovering

If you make changes to repair the flow and you want to continue normally, use the `exit` control flow statement over the `onBack` block.

In these cases, the next time the flow go back to the `onBack` block it will recover seeing the changes made the last time. For example:

```lxm
var test = 0

onBack {
    if(test < 3) {
        test += 1
        exit
    }
}
```

In this example, the flow will recover whenever the backtracking reaches this `onBack` block until the `test`'s value is greater or equal than 3. In this case the backtracking continues.  

> **Note**: make sure you don't cause an infinite loop.

#### Abbreviation

Because this pattern is very common, there is a syntactic sugar to write it easily.

```lxm
-- original

onBack {
    if -+ condition +- {
        -- modifications to recover the flow
        exit
    }

    -- code when it cannot recover the flow
}

-- syntactic sugar

onBack if -+ condition +- {
    -- modifications to recover the flow
    -- the 'exit' is not necessary
}
else {
    -- code when it cannot recover the flow
}
```

> **Note**: you can use any of the following statements, conditional (`if` and `unless`) and selective (`when`).
