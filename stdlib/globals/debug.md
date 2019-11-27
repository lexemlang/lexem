
# Table of contents

- [Table of contents](#table-of-contents)
- [Methods](#methods)
  - [`.pause()`](#pause)
  - [`.log(message: Any)`](#logmessage-any)
  - [`.log(message: Any, tag:String)`](#logmessage-any-tagstring)
  - [`.throw(message: String)`](#throwmessage-string)

# Methods

## `.pause()`

Pauses the analyzer. When the analysis is resumed, it starts after the call.

```lxm
Debug.pause()
```

## `.log(message: Any)`

Logs a message in the console.

```lxm
Debug.log("This is the message")
```

### Parameters

- **`message`**: the message to log.

### Examples

```lxm
let number = 5
Debug.log("The number is: " + number)
```

## `.log(message: Any, tag:String)`

Logs a message in the console using the specified tag.

```lxm
Debug.log("This is the message", "tag")
```

### Parameters

- **`message`**: the message to log.

### Examples

```lxm
let number = 5
Debug.log("The number is: " + number, "tag")
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
