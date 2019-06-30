# Index

- [Index](#Index)
- [Comments](#Comments)

# Comments

Comments are an useful utility that helps to document the code.

There are two types of comments. A single-line comment started with `#-` and any text until an end-of-line character:

```lexem
#- this is a single-line comment
```

And a multiline version enclosed between `#+` and  `+#`:

```lexem
#+ this is a
multiline comment +#
```

Multiline version allows using more than one `+` to embed another comments:

```lexem
#++ this is the main comment
    #+ this is a
    multiline comment +#
the end of main comment ++#
```
