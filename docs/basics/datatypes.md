---
icon: lucide/file-text
---

# Data Types

## Which are the Data Types in Swift

There are many complex variables in Swift but we mainly use four:

- Array (the main Data Type in Swift)
- Set
- Dictionary
- Enum

Each one has benefits and drawbacks which we'll see a bit later.

---

## Array

### What is an array
The array is the most common Data Type in Swift. They are a complex Data Type, which is like a List. They remember the order you insert values into them and they allow duplicates.

### How to declare an array
You'll see that there are many ways to declare arrays in Swift. For the examples we'll use `Int` arrays.

=== "Implicit"

    ```swift
    var intArray = [1, 3, 5, 2, 6]
    ```

=== "Declare the type"

    ```swift
    var intArray = Array<Int>()
    ```

=== "Much simpler way to declare it"

    ```swift
    // As they are so common you can use Brackets with the type
    var intArray = [Int]()
    ```

### How to use an array
Arrays have multiple functions and properties:

- `append(<value>)` => add a value at the end of the array
- `remove(at: <pos>)` => remove a value at a certain position of the array, the <pos> is an `Int`
- `removeAll()` => remove all the elements of an array
- `count` => property that returns the number of elements of an array
- `reversed()` => returns a collection with the elements in the reversed order
- `sorted()` => returns an array sorted (for numbers from -infinity to +infinity, and for strings in alphabetical order)
- `contains(<element>)` => `element` type is the type of the array, returns true if the element is in the array, false otherwise

---

## Set

### What is a set
A Set is a complex Data Type that stores unique values of the same type in a collection with no defined ordering. They are extremely fast for looking up if an item exists, but they **do not allow duplicates** and do not remember the order you insert values into them.

### How to declare a set
Unlike arrays, sets must be explicitly declared as a `Set`, otherwise Swift will infer it as an array. We'll use `Int` sets for the examples.

=== "Implicit with values"

    ```swift
    // You must specify ': Set' so Swift doesn't create an Array
    var intSet: Set = [1, 3, 5, 2, 6]
    ```

=== "Declare the type"

    ```swift
    var intSet = Set<Int>()
    ```

=== "Explicit typing"

    ```swift
    var intSet: Set<Int> = []
    ```

### How to use a set
Sets share some functions with arrays, but have their own specificities:

- `insert(<element>)` => add a value to the set (it will be ignored if it already exists)
- `remove(<element>)` => remove a specific value from the set
- `removeAll()` => remove all the elements of a set
- `count` => property that returns the number of elements of a set
- `contains(<element>)` => returns true if the element is in the set, false otherwise
- `sorted()` => returns a sorted **Array** containing the set's elements
- `intersection(<another_set>)` => creates a new set with only the values common to both sets

---

## Dictionary

### What is a dictionary
A Dictionary is a complex Data Type that stores associations between keys of the same type and values of the same type in a collection with no defined ordering. Each value is associated with a **unique key**, which acts as an identifier for that value within the dictionary.

### How to declare a dictionary
Dictionaries use brackets like arrays, but require key-value pairs separated by a colon `:`. We'll use `String` for keys and `Int` for values in the examples.

=== "Implicit"

    ```swift
    var scoresDict = ["Pierre": 20, "Alice": 18]
    ```

=== "Declare the type"

    ```swift
    var scoresDict = Dictionary<String, Int>()
    ```

=== "Much simpler way to declare it"

    ```swift
    // Using Brackets with the types for Key and Value
    var scoresDict = [String: Int]()
    ```

### How to use a dictionary
Dictionaries are manipulated using their keys:

- `dict[<key>] = <value>` => add a new key-value pair, or update the value if the key already exists
- `dict[<key>] = nil` => remove a key-value pair from the dictionary
- `updateValue(<value>, forKey: <key>)` => alternative way to update/add a value, returns the old value if it existed
- `removeValue(forKey: <key>)` => alternative way to remove a value, returns the removed value
- `removeAll()` => remove all key-value pairs
- `count` => property that returns the number of key-value pairs
- `keys` => property that returns a collection of all the keys in the dictionary
- `values` => property that returns a collection of all the values in the dictionary

---

## Enum

### What is an enum
An enumeration (or enum) defines a common type for a group of related, mutually exclusive values. It allows you to work with these values in a type-safe way, preventing you from accidentally using invalid strings or numbers. Swift enums are incredibly powerful and can even store extra data or have their own functions.

### How to declare an enum
There are several ways to define enums depending on how much information they need to hold. 

=== "Basic Enum"

    ```swift
    enum CompassPoint {
        case north
        case south
        case east
        case west
    }
    // You can also write it on a single line: case north, south, east, west
    ```

=== "With Raw Values"

    ```swift
    // Enums can have pre-populated underlying values (like Strings or Ints)
    enum Weekday: String {
        case monday = "Monday"
        case tuesday = "Tuesday"
        // If you omit the value, Swift automatically uses the case name as the string
        case wednesday
    }
    ```

=== "With Associated Values"

    ```swift
    // Enums can store custom variables alongside their cases
    enum Barcode {
        case upc(Int, Int, Int, Int)
        case qrCode(String)
    }
    ```

### How to use an enum
Enums are heavily used with `switch` statements and rely on a shorthand dot syntax once the type is known:

- `var direction = CompassPoint.north` => initialize a variable with an enum case
- `direction = .south` => once the variable's type is known by Swift, you can omit the enum name and just use the dot `. `
- `switch` statement => the most common way to check an enum's value. Swift is extremely safe and forces your `switch` to be **exhaustive** (you must explicitly handle every single case).
- `rawValue` => property used to get the underlying value of an enum declared with raw types (e.g., `Weekday.monday.rawValue` returns `"Monday"`)
- `CaseIterable` => if you make your enum conform to this protocol (e.g., `enum CompassPoint: CaseIterable`), you can use the `CompassPoint.allCases` property to get an Array of all available cases