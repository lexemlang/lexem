# Table of contents

- [Index](#index)
- [Comments](#comments)

# Comments

Comments are an useful utility that helps to document the code.

There are two types of comments. A single-line comment started with `--` and any text until an end-of-line character:

```lexem
-- this is a single-line comment
```

And a multiline version enclosed between `#-` and  `-#`:

```lexem
#- this is a
multiline comment -#
```

Multiline version allows using more than one `-` to embed another comments:

```lexem
#-- this is the main comment
    #- this is a
    multiline comment -#
the end of main comment --#
```

Moreover, you can close them immediately after opening it, just putting a sharp (`#`) after the opening dashes (`-`):

```lexem
#-#
#--#
#---#
```

This kind of syntax allows to quickly comment a piece of code.
To do that, you must surround the code with a multiline comment with at least two dashes (`#--`, `--#`).
This way, if you want to comment the code just leave it like this, but if you want to enable it put a sharp (`#`) immediately after the opening dashes (`#--`),
closing the multiline comment at the beginning and converting the closing into a single line comment.

For example:

```lexem
-- Commented
#--
fun code() {
    #- This is an experimental code that wou want
    to switch quickly to perform any kind of tests -#

    ...
}
--#

-- Enabled
#--#
fun code() {
    #- This is an experimental code that wou want
    to switch quickly to perform any kind of tests -#

    ...
}
--#
```
