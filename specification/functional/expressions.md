
# Table of contents

- [Table of contents](#table-of-contents)
- [Functional expressions](#functional-expressions)
  - [Indexers](#indexers)
    - [Slices](#slices)
  - [Accesses](#accesses)
  - [Function calls](#function-calls)
  - [Operators](#operators)
    - [Unitary operators](#unitary-operators)
    - [Binary operators](#binary-operators)
    - [Chained binary operators](#chained-binary-operators)
    - [Assignments](#assignments)

# Functional expressions

The expressions are logical and arithmetic operations that modify elements and generates results thanks to applying certain transformations to their inputs.

They can be built with the following components:

## Indexers

The indexers get elements inside another elements using the following syntax:

```lexem
element[index]
```

TIndexers can access to different values depending on the element over it is used:

| Element type | Accepts | Meaning |
|:------------:|:-------:|:--------|
| `String` | `Integer` | Gets or sets the character at the specified position. |
| `Interval` | `Integer` | Gets the number at the specified position. |
| `BitList` | `Integer` | Gets or sets the bit at the specified position as a logic value. |
| `List` | `Integer` | Gets or sets the element at the specified position. |
| `Object` | `String` | Gets or sets the value associated to the specified key. |
| `Map` | `Any` | Gets or sets the value associated to the specified key. |

> **Note**: when an index does not exist, it returns a `nil`.

### Slices

Some indexers can use intervals as indexes instead of just `Integer`s to obtain each of those elements at once.

| Type | Meaning |
|:----:|:--------|
| `String` | Gets a new `string` with only the specified set of characters. |
| `Interval` | Gets a new `Interval` with only the specified set of numbers. |
| `BitList` | Gets a new `BitList` with only the specified set of bits. |
| `List` | Gets a new `list` with only the specified set of elements. |

```lexem
var string = "Hello"
var string3 = string[itv![1..3]]

-- string2 == "ell"
```

## Accesses

Accesses are a simplification of indexers meant to get the properties of an object.

An identifier, any type of string literal or an escaped expression, must be used to specify the name of the property to get:

```lexem
var object = {a: 1, b: 2, c: 3}

var x = object.a        -- x == 1
var y = object."b"      -- y == 2
var z = object.\("c")   -- z == 3
```

Moreover, accesses let us to get the methods or properties of any type from their prototypes. For example:

```lexem
var string = "Hello, world!"
string.replace("world", by: "Lexem") -- replace one word by another

var num = 9
num.sign                             -- gets the sign of the number
```

> **Note**: when an access does not exist, it returns a `nil`.

## Function calls

When the code of a function has to be executed, the function must be called. To perform the call, it is necessary to write the arguments following this order:

1. Positional arguments.
2. Named arguments specifying key-value pairs.
3. Spread arguments to deconstruct them into a positional or named, depending on the type of the value.
   - Lists are deconstructed into positional arguments.
   - Objects and maps are deconstructed into named arguments.

```lexem
funtion(positionalArguments, namedArguments, spreadArguments) {}
```

For example, a full call is like:

```lexem
function(positional1, positional2, named1: value1, named2:value2, ...{spread_object: as_named}, ...[spread, list, as, positional])
```

Finally, it is necessary to mention two variables that are set by default inside every function.

1. When the called function belongs to an object, that object is passed as another argument called `this`.

  ```lexem
  let function = fun(){
    log(this)
  }
  function()  -- this == nil

  let container = {function}
  container.function()  -- this == container

  -- equivalent to --

  function(this: nil)

  container.function(this: container)
  ```

  The first call is `nil` because there's no container while in the last one the function is called from inside an object which is its container.
  The container has priority over an argument called `this`, so it will not be overwritten, in cases like:

  ```lexem
  let container = {function(){ }}
  container.function(this:3)  -- this == container

  -- equivalent to --
  
  container.function(this: 3, this: container)
  ```

2. All arguments are accesible inside the function throught the variable `arguments`.

```lexem
let function = fun(){}
function()                            -- arguments == {positional: [], named: {}}
function(1, 2)                        -- arguments == {positional: [1, 2], named: {}}
function(a: 5, b: 6)                  -- arguments == {positional: [], named: {a: 5, b: 6}}
function(1, a: 5, ..[2, 3], ..{b: 6}) -- arguments == {positional: [1, 2], named: {a: 5, b: 6}}
```

> **Note**: if an argument's name is set more than once, the last takes priority over the rest.

## Operators

There are different types of operators classified by the number of operands they use.

### Unitary operators

| Operator | Used over types | Meaning |
|:--------:|:---------------:|:--------|
|`!`|`any`| Logic negation over the truthiness of an element. |
|`~`|`BitList`| Bitwise negation i.e. negates all bits. |
|`+`|`Integer`, `Float`| Arithmetic affirmation. |
|`-`|`Integer`, `Float`| Arithmetic negation. |

This operators have the maximum priority of all of the operators. Moreover, to change the priority of any kind of expression use the parenthesis:

```lexem
(expression)
```

### Binary operators

| Category | Operator | Used over ... | Meaning |
|:--------:|:--------:|:-------------:|:--------|
|Multiplicative|`*`|`Integer`, `Float`| Product. |
||`/`|`Integer`, `Float`| Division. |
||`//`|`Integer`, `Float`| Integer division. |
||`%`|`Integer`, `Float`| Reminder of integer division. |
|Additive|`+`|`Integer`, `Float`| Addition. |
||`-`|`Integer`, `Float`| Subtraction. |
|Shift|`>>`|`BitList`| Shifts the bits n positions to right. |
||`<<`|`BitList`| Shifts the bits n positions to left. |
||`/>`|`BitList`| Rotates the bits n positions to right. |
||`</`|`BitList`| Rotates the bits n positions to left. |
|Logic|`&`|`BitList`, `Logic`| Logic AND bit a bit. |
||`\|`|`BitList`, `Logic`| Logic OR bit a bit. |
||`^`|`BitList`, `Logic`| Logic XOR bit a bit. |

Categories are ordered from high to less priority. Moreover, operators in the same category have the same priority.

### Chained binary operators

This operators are binary operators that works differently whether they are alone or grouped.

| Category | Operator | Used over ... | Meaning |
|:--------:|:--------:|:-------------:|:--------|
|Relational|`>`|`Integer`, `Float`| Greater than. |
||`<`|`Integer`, `Float`| Lower than. |
||`>=`|`Integer`, `Float`| Greater or equal than. |
||`<=`|`Integer`, `Float`| Lower or equal than. |
||`==`|`any`| Equal than. |
||`!=`|`any`| Different of. |
||`===`|`any`| Identity. Check that both operands are the same object comparing the reference. For primitives it is the same as `==`. |
||`!==`|`any`| No-identity. Check that both operands are different objects comparing the reference. For primitives it is the same as `!=`. |
|Conditional|`and`|`any`| Evaluates the left operand and returns it if it is `falsity`, otherwise returns the right operand. |
||`or`|`any`| Evaluates the left operand and returns it if it is `truthy`, otherwise returns the right operand. |
||`xor`|`any`| Evaluates the left operand and if it is `truthy` returns the right operand, otherwise if left is `falsity`, evaluates the right operand returning the left value if right is `falsity` or `nil` if both are `truthy`. |

Categories are ordered from high to less priority and operators in the same category have the same priority. All of these categories have less priority than normal binary operators.

These operators can be chained if they are under the same category:

```lexem
a < b == c >= d
```

This expression means the same as the following because intermediate operands are evaluated just once.

```lexem
var aux = b
var aux2 = c
(a < aux) and (aux == aux2) and (aux2 >= d)
```

Conditional operands behave like the table shows:

```lexem
a and b and c
a or  b or  c
a xor b xor c
```

| a | b | c | and | or  | xor |
|:-:|:-:|:-:|:---:|:---:|:---:|
| F | F | F |  a  |  c  |  c  |
| F | F | T |  a  |  c  |  c  |
| F | T | F |  a  |  b  |b(c) |
| F | T | T |  a  |  b  |F(c) |
| T | F | F |  b  |  a  |a(c) |
| T | F | T |  b  |  a  |F(c) |
| T | T | F |  c  |  a  |F(b) |
| T | T | T |  c  |  a  |F(b) |

`F` means falsity and `T` means truthy. `x(y)` means that the returned value is `x` and that the expression has been analyzed until the `y` operand, so the rest operands after that have been skipped.

### Assignments

| Category | Operator | Used over ... |
|:--------:|:--------:|:-------------:|
|Assignment|`=`|`Any`|
|Multiplicative|`*=`|`Integer`, `Float`|
||`/=`|`Integer`, `Float`|
||`//=`|`Integer`, `Float`|
||`%=`|`Integer`, `Float`|
|Additive|`+=`|`Integer`, `Float`|
||`-=`|`Integer`, `Float`|
|Shift|`>>=`|`BitList`|
||`<<=`|`BitList`|
||`/>=`|`BitList`|
||`</=`|`BitList`|
|Logic|`&=`|`BitList`, `Logic`|
||`|=`|`BitList`, `Logic`|
||`^=`|`BitList`, `Logic`|
|Conditional|`and=`|`Any`|
||`or=`|`Any`|
||`xor=`|`Any`|

Every assigment with an operator is equivalent to:

```lexem
left op= right

-- equivalent to --

left = (left op right)
```

> **Note**: All the operators return its value. So they can be used as a right expressions of another assigment.
