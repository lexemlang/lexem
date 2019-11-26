
# Table of contents

- [Table of contents](#table-of-contents)
- [Methods](#methods)
  - [`.pause()`](#pause)
  - [`.throw(message: String)`](#throwmessage-string)

# Methods

## `.pause()`

Pauses the analyzer. When the analysis is resumed, it starts after the call. 

```lxm
Debug.pause()
```

## `.throw(message: String)`

Throws an error finishing the analyzer.

```lxm
Debug.throw("This is the message")
```

### Parameters

- **`message`**: the message of the error.

### Errors

- **`CustomError`**: the error thrown.

### Examples

```lxm
let number = ...
if (number < 0) {
    Debug.throw("The number cannot be negative")
}
```
