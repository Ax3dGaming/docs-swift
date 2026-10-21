---
icon: lucide/variable
---

# Simple variables

## How to create variables and constants

### Variables

You use `var` to create a variable. Its value can be changed later.

```swift
// Needs either an initial value or an explicit type
var myVariable = "Hello"
var myOtherVariable: String
```

### Constants

You use `let` to create a constant. Its value cannot be changed once set.

```swift
let myConstant = 10
```

## Simple variable types

### Integer

To create an integer you use `Int` or declare it implicitly.

=== "Implicitly"

    ```swift
    var intVariable = 0
    ```

=== "Declare the type"

    ```swift
    var intVariable: Int = 0
    ```

### Double

To create a double (a floating-point number with decimal places) you use `Double` or declare it implicitly.

=== "Implicitly"

    ```swift
    var doubleVariable = 0.0
    ```

=== "Declare the type"

    ```swift
    // With this you can declare a Double without any number after the decimal point
    var doubleVariable: Double = 0
    ```

### String

To create a string you can do exactly the same, use `String` or declare it implicitly.

=== "Implicitly"

    ```swift
    var stringVariable = "Hello World!"
    ```

=== "Declare the type"

    ```swift
    var stringVariable: String = ""
    ```

Special properties and functions:

- `count` => property that returns the number of characters in the `String` (no parentheses).
- `sorted()` => function that returns an Array of characters sorted in alphabetical order (`[Character]`). To make it a String again, you must use `String(stringVariable.sorted())`.

### Boolean

The final simple variable type, you can do the same as above.

=== "Implicitly"

    ```swift
    var boolVariable = true
    ```

=== "Declare the type"

    ```swift
    var boolVariable: Bool = false
    ```

Special functions:

- `toggle()` => changes the value, from `true` to `false` and the other way around.

## Operators

Like any other language, there are many operators which can be used on simple variables.

- Operator `+` is available on `Int`, `Double`, and `String` (on strings, it concatenates them).
- Operator `-` is available on `Int`, `Double`.
- Operator `*` is available on `Int`, `Double`.
- Operator `/` is available on `Int`, `Double`.

As you may notice, there aren't any arithmetic operators on `Bool` because you can't add `Bool` values together. However, there are logical operators:

- Operator `!` can invert a `Bool`: if the value is `true` it makes it `false`.
- Operator `&&` (AND) returns `true` if both booleans are `true`.
- Operator `||` (OR) returns `true` if at least one boolean is `true`.