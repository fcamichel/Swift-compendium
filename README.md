# Swift compendium

*Table of content*

- [Simple types](#simple-types)
  * [Variables](#variables)
  * [Strings and integers](#strings-and-integers)
  * [Multi-line strings](#multi-line-strings)
  * [Doubles and booleans](#doubles-and-booleans)
  * [String interpolation](#string-interpolation)
  * [Constants](#constants)
  * [Type annotations](#type-annotations)
- [Complex Types](#complex-types)

## Simple types

### Variables

```
var str = "Hello, playground"
```

That creates a new variable called **str**, giving it the value "Hello, playground".

Because **str** is a variable we can change it:

```
str = "Goodbye"
```

We don’t need **var** the second time because the variable has already been created – we’re just changing it.

### Strings and integers

Swift is what’s known as a type-safe language, which means that every variable must be of one specific type. 

```
var age = 38
```

That holds a whole number, so Swift assigns the type **Int** – short for "integer".

If you have large numbers, Swift lets you use underscores as thousands separators – they don’t change the number, but they do make it easier to read. For example:

```
var population = 8_000_000
```

Strings and integers are different types, and they can’t be mixed. So, while it’s safe to change **str** to "Goodbye", I can’t make it 38 because that’s an **Int** not a **String**.

### Multi-line strings

Standard Swift strings use double quotes, but you can’t include line breaks in there.

If you want multi-line strings you need slightly different syntax: start and end with three double quote marks, like this:

```
var str1 = """
This goes
over multiple
lines
"""
```

Swift is very particular about how you write those quote marks: the opening and closing triple must be on their own line, but opening and closing line breaks won’t be included in your final string.

If you only want multi-line strings to format your code neatly, and you don’t want those line breaks to actually be in your string, end each line with a **\\**, like this:

```
var str2 = """
This goes \
over multiple \
lines
"""
```

### Doubles and booleans

Two other basic types of data in Swift are doubles and booleans, and you’ll be using them a lot.

"Double" is short for "double-precision floating-point number", and it’s a fancy way of saying it holds fractional values such as 38.1, or 3.141592654.

Whenever you create a variable with a fractional number, Swift automatically gives that variable the type **Double**. For example:

```
var pi = 3.141
```

Doubles are different from integers, and you can’t mix them by accident.

As for booleans, they are much simpler: they just hold either true or false, and Swift will automatically assign the boolean type to any variable assigned either true or false as its value.

For example:

```
var awesome = true
```

### String interpolation

You can place any type of variable inside your string – all you have to do is write a backslash, **\\**, followed by your variable name in parentheses. For example:

```
var score = 85
var str = "Your score was \(score)"
```

You can do this as many times as you need, making strings out of strings if you want:

```
var results = "The test results are here: \(str)"
```

String interpolation isn’t just limited to placing variables – you can actually run code inside there.

### Constants

Very often you want to set a value once and never change it, and so we have an alternative to the var keyword called **let**.

The **let** keyword creates constants, which are values that can be set once and never again. For example:

```
let taylor = "swift"
```

You should always use **let** unless you specifically want to change a value.

### Type annotations

Swift assigns each variable and constant a type based on what value it’s given when it’s created.

If you want you can be explicit about the type of your data rather than relying on Swift’s type inference, like this:

```
let album: String = "Reputation"
let year: Int = 1989
let height: Double = 1.78
let taylorRocks: Bool = true
```

## Complex Types

