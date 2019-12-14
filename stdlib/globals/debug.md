
# Table of contents

- [Table of contents](#table-of-contents)
- [Methods](#methods)
  - [.pause() -&gt; Nil](#pause--gt-nil)
  - [.log(message: Any) -&gt; Nil](#logmessage-any--gt-nil)
  - [.log(message: Any, tag: String) -&gt; Nil](#logmessage-any-tag-string--gt-nil)
  - [.throw(message: String)](#throwmessage-string)
  - [.throw(message: String, tag: String)](#throwmessage-string-tag-string)

# Methods

## `.pause() -> Nil`

Pauses the analyzer. When the analysis is resumed, it starts after the call.

```lxm
Debug.pause()
```

## `.log(message: Any) -> Nil`

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

## `.log(message: Any, tag: String) -> Nil`

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

## `.throw(message: String, tag: String)`

Throws an error finishing the analyzer.

```lxm
Debug.throw("This is the message", "tag")
```

### Parameters

- **`message`**: the message of the error.

### Errors

- **`CustomError`**: the error thrown.

### Examples

```lxm
let number = ...
if (number < 0) {
    Debug.throw("The number cannot be negative", "tag")
}
```
