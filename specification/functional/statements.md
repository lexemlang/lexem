
# Index

- [Index](#Index)
- [Statements](#Statements)
  - [Blocks of code](#Blocks-of-code)
    - [Inside expressions](#Inside-expressions)
    - [Control statements](#Control-statements)
  - [Variable declaration](#Variable-declaration)
    - [Re-declarations](#Re-declarations)
    - [Assigns](#Assigns)
    - [Destructuring](#Destructuring)
      - [Lists](#Lists)
      - [Objects](#Objects)
      - [Mixing variables and constants](#Mixing-variables-and-constants)
  - [Truth and falsity](#Truth-and-falsity)
  - [Conditional statements](#Conditional-statements)
    - [Conditional expressions](#Conditional-expressions)
  - [Selective statements](#Selective-statements)
    - [Control statements](#Control-statements-1)
  - [Loop statements](#Loop-statements)
    - [Infinite loops](#Infinite-loops)
    - [Conditional loops](#Conditional-loops)
    - [Iterator loops](#Iterator-loops)
    - [Control statements](#Control-statements-2)
    - [Finalization](#Finalization)

# Statements

Lexem has several statements to control the flow of the code. Every one of them creates a context in its body.

## Blocks of code

A block of code is a group of expressions and statements that are grouped and works together. Moreover, blocks create a new context for its own code.

Their syntax is the following and are widely used across the entire language:

```lexem
{'tag body}
```

They optionally can have a tag to identify them for the control statements.

### Inside expressions

The block statements can also be used inside an expression. In these cases the value of the last statement executed is returned as the result of the block.

### Control statements

There are control statements that can be used inside blocks:

| Statement | Meaning |
|:---------:|:--------|
|`exit'tag`|Stops the execution of the specified block.|
|`exit'tag expression`|Stops the execution of the specified block returning a value.|

## Variable declaration

To define a variable is as easy as choosing a name and give them a value with the following scheme:

```lexem
var name = value
```

This creates a mutable value in the current context, so it can be accessed by `context.name`.

To prevent a variable to be mutable i.e. to define a **constant**, use the following schema:

```lexem
let name = value
```

### Re-declarations

Re-declare a variable is the same as assigning a new value to it but only if both declarations are in the same context. In any other case it defines a new variable in the current context.

```lexem
var x = 3
-- x == 3

var x = 6
-- x == 6

{
    var x = "alfa"
    -- x == "alfa"
}

-- x == 6
```

> **Note**: constants can't be re-declared because... well, they are constants!

### Assigns

Assign expressions can declare a new mutable variable if it does not exist before, but it must be bared in mind that if the variable exists in the current context or any of its parents, it will be replaced with all of its side effects, like throwing an error if it is a constant.

```lexem
-- x == nil

x = 3
-- x == 3

{
    x = "alfa"
    -- x == "alfa"
}

-- x == "alfa"
```

### Destructuring

Destructuring is an useful utility that help to decompose complex objects and lists into its semantic pieces easily.

#### Lists

To destructure a list it is necessary to use the following syntax:

```lexem
let list = [1, 2, 3, 4]     -- list to be destructured

let (el1) = list            -- gets first element
var (el1, el2) = list       -- gets first and second elements
let (el1, _, el3) = list    -- gets first and third elements
let (el1, _2, el4) = list   -- gets first and fourth elements
var (el1, ..rest) = list    -- gets first element and the rest are stored in rest
var name(...) = list        -- destructures 'list' using one of the above rules but also creates a new variable called 'name' with the value of list.
```

As it is shown above, the skip operator (`_`) allows to skip a certain number of elements of the list, setting a number after the underscore, while the spread operator (`..`) allows to store the rest elements inside a new list.

Moreover, there is another type that destructures a value using the above rules but also creates a new variable called for that value:

```lexem
var name(...) = list

# is equivalent to

var (...) = list
var name = list
```

> **Note**: the rest operator `..name` can only be set once at the end of the parenthesis.

#### Objects

To destructure an object it is necessary to use the following syntax:

```lexem
let object = {a: 1, b: 2, c: 3} -- object to be destructured

let (a) = object          -- gets the a element
var (a, b) = object       -- gets the a and b elements
let (b, ..rest) = object  -- gets the b element and the rest are stored in rest
var (a as new) = object   -- gets the a element but renames it to new
```

As it is shown above, the spread operator (`..`) allows to store the rest elements inside a new object while the rename operator (`as`) allows to rename the element got from the object with a new name.

Moreover, there is another type that destructures a value using the above rules but also creates a new variable called for that value:

```lexem
var name(...) = object

# equivalente to

var (...) = object
var name = object
```

> **Note**: the rest operator `..name` can only be set once at the end of the parenthesis.

#### Mixing variables and constants

The `var` destructuring allows to define variables and constants at the same time, using this for lists:

```lexem
let list = [1, 2, 3, 4]     -- list to be destructured

var (el1, #el2) = list      -- el1 is a variable and el2 is a constant
var (el1, ..#rest) = list   -- el1 is a variable and rest is a constant

var #name(...) = list       -- name is a constant but the inner rules are not affected
```

And this for objects:

```lexem
let object = [1, 2, 3, 4]  -- list to be destructured

var (a, #b) = object       -- a is a variable and b is a constant
let (b, ..#rest) = object  -- b is a variable and rest is a constant
var (a as #new) = object   -- new is a constant

var #name(...) = object    -- name is a constant but the inner rules are not affected
```

## Truth and falsity

Every value can be checked in the statement's conditions for its truthfulness. The conversion rule is that all values are `true` less `false` and `nil`.

## Conditional statements

As in any other language, conditional statements, also known as _if_ statements, are used with the following syntax:

```lexem
if condition {body}
unless condition {body}
```

The `if` variant executes its body when the truthfulness of its condition results in `true` while the `unless` variant requieres a `false`. In fact,  `unless` conditions are equivalent to `if` conditions as long as they are negated: `unless == !if`.

Parenthesis in the conditions are optional and only used to improve readability.

Moreover, these statements have `else` clauses which are executed when the condition does not match. Can be combined to create what is known as `else-if` clauses:

```lexem
if condition {body}
else if condition {body}
else unless condition {body}
else {body}
```

### Conditional expressions

The conditional statements can also be used inside an expression. In these cases it is always required that the conditional returns a value, so the value of the last statement executed is returned as a result.

If the conditional expression has no `else` clause and the condition does not match, a `nil` value is returned.

## Selective statements

The selective statements, also known as _switch_/_match_/_when_ statements, are used with the following syntax:

```lexem
when condition {'tag
    pattern, pattern {
        body
    }
}
```

The tag is optional and defines a name for the whole `when` statement to identify it. The condition is also optional, so in case it is omitted the value used for the patterns of the `when` statement is `nil`.

The `when` statements works evaluating the condition against each of the options until one of them matches and executes its body. Each option can have one or more patterns acting as its conditions.

The allowed patterns are:

- `expression conditional {body}`: compares `when`'s condition with the result of the expression. If they match, the conditional is executed and if it also matches then the body is executed. The conditional is optional.

    ```lexem
    let num = 4
    when num {
        1 {}
        2 {}
        itv![2..8] if num.isEven {}
        itv![2..8] if num.isOdd {}
    }
    ```

- `conditional {body}`: matches only if the conditional matches. It is normally used to set a pure conditional case.

    ```lexem
    let num = 4
    when num {
        if num > 4 {}      -- pure conditional
        unless num > 4 {}  -- pure conditional
    }
    ```

- `else {body}`: matches always. It is normally used to set a default case.

    ```lexem
    let num = 4
    when num {
        3 {}
        if num > 5 {}
        else {}        -- default case
    }
    ```

    > **Note**: set it at the end or those patterns after this one will be ignored.
    
- `var name conditional {body}`: defines a variable whose value is the `when`'s condition value; then executes the conditional. The `let` declaration can also be used. The variable can be used inside its condition and body.

    ```lexem
    let num = 4
    when num + 40 / 10 {
        let value if value < 4 {
            value     -- 8
        }
    }
    
    when {a: 2, b: 3} {
        var (a) if a > 4 {
            a     -- 2
        }
        let (b) {}
    }
    ```
    
    It can also be used with destructuring. 
    > **Note**: if condition is omitted, the pattern matches always.

### Control statements

To control the execution of `when` statements, there are the following statements:

| Statement | Meaning |
|:---------:|:--------|
|`exit`|Stops the flow control statement immediately above.|
|`exit expression`|Stops the flow control statement immediately above returning a value.|
|`exit'tag`|Stops the execution of the specified `when`.|
|`exit'tag expression`|Stops the execution of the specified `when` returning a value.|

## Loop statements

A loop is a repetition of a certain code. There are the following types:

### Infinite loops

Loops that are repeated indefinitely.

```lexem
repeat {'tag body}
repeat name {'tag body}
```

Using the _indexed_ pattern (`repeat name`), each iteration of the loop increases the variable by one.

### Conditional loops

Loops that are repeated whenever their condition match. There are two variants:

- `while`: executes its body as long as its condition is `true`.
- `until`: executes its body as long as its condition is `false`.

```lexem
while condition {'tag body}
until condition {'tag body}

repeat name while condition {'tag body}
repeat name until condition {'tag body}
```

Using the _indexed_ pattern (`repeat name`) each iteration of the loop increase the variable by one.

The pattern known as `do-while` loops are not supported directly, but can be easily implemented like:

```lexem
-- do-while
repeat {
    body

    unless condition {
        exit
    }
}

-- do-until
repeat {
    body

    if condition {
        exit
    }
}
```

### Iterator loops

Loops that are repeated once for each element of a collection.

```lexem
for index, value in expression {'tag body}  -- normal
for index, (...) in expression {'tag body}  -- destructuring

repeat name for index, value in expression {'tag body}  -- normal
repeat name for index, (...) in expression {'tag body}  -- destructuring
```

Using the _indexed_ pattern (`repeat name`) each iteration of the loop increase the variable by one. On the other hand, the `index` section is optionally.

In each iteration, the variable of the `for` loop is filled with the current value of the collection and the `index` is filled with the index or key used to get the value inside the collection. The index variable can be omitted if it is not necessary.

### Control statements

Every loop accepts a tag to identify it with the objective of control its execution:

| Statement | Meaning |
|:---------:|:--------|
|`exit`|Stops the flow control statement immediately above.|
|`exit expression`|Stops the flow control statement immediately above returning a value.|
|`next`|Stops the current iteration and continues with the next iteration of the loop statement immediately above.|
|`redo`|Restarts the current iteration of the loop statement immediately above.|
|`restart`|Restarts from the beginning the whole loop statement immediately above.|
|`exit'tag`|Stops the execution of the specified loop.|
|`exit'tag expression`|Stops the execution of the specified loop returning a value.|
|`next'tag`|Stops the current iteration and continues with the next iteration of the specified loop.|
|`redo'tag`|Restarts the current iteration of the specified loop.|
|`restart'tag`|Restarts from the beginning the specified loop.|

### Finalization

All loops can have finalization blocks that are executed only if its condition is satisfied:

- `last` block: it is executed as the last iteratior only if the loop exits normally i.e. without using an `exit` statement but only after executing at least one time.
- `else` block: it is executed only if the loop fails before executing once its body.

For example:

```lexem
while cond {
    body
}
else {
    body    -- Only executes if cond is false.
}


for num in [1, 2, 3] {
    body
}
last {
    body    -- Only executes when the iterator finish not by an exit.
}


for key, value in obj {
    body
}
last {
    body    -- Only executes when the iterator finish not by an exit.
}
else {
    body    -- Only executes if obj is empty.
}


repeat {
    body
}
last {
    body    -- Never executes because the loop will always be finished by an exit.
}
```

> **Note**: the order must be always the `last` block and finally the `else` block.
