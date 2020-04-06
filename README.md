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
  * [Arrays](#arrays)
  * [Sets](#sets)
  * [Tuples](#tuples)
  * [Arrays vs sets vs tuples](#arrays-vs-sets-vs-tuples)
  * [Dictionaries](#dictionaries)
  * [Dictionary default values](#dictionary-default-values)
  * [Creating empty collections](#creating-empty-collections)
  * [Enumerations](#enumerations)
  * [Enum associated values](#enum-associated-values)
  * [Enum raw values](#enum-raw-values)
- [Operators and conditions](#operators-and-conditions)


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

### Arrays

Arrays are collections of values that are stored as a single value. For example, John, Paul, George, and Ringo are names, but arrays let you group them in a single value called The Beatles.

In code, we write this:

```
let john = "John Lennon"
let paul = "Paul McCartney"
let george = "George Harrison"
let ringo = "Ringo Starr"

let beatles = [john, paul, george, ringo]
```

That last line makes the array: it starts and ends with brackets, with each item in the array separated by a comma.

You can read values from an array by writing a number inside brackets. Array positions count from 0, so if you want to read “Paul McCartney” you would write this:

```
beatles[1]
```

Be careful: Swift crashes if you read an item that doesn’t exist. For example, trying to read **beatles[9]** is a bad idea.

Note: If you’re using type annotations, arrays are written in brackets: **[String]**, **[Int]**, **[Double]**, and **[Bool]**.

```
var scores: [Int] = [10, 12, 9]
```

### Sets

Sets are collections of values just like arrays, except they have two differences:

1. Items aren’t stored in any order; they are stored in what is effectively a random order.
2. No item can appear twice in a set; all items must be unique.

You can create sets directly from arrays, like this:

```
let colors = Set(["red", "green", "blue"])
```

Because they are unordered, you can’t read values from a set using numerical positions like you can with arrays.

If you try to insert a duplicate item into a set, the duplicates get ignored. For example:

```
let colors2 = Set(["red", "green", "blue", "red", "blue"])
```

The final colors2 set will still only include red, green, and blue once.

### Tuples

Tuples allow you to store several values together in a single value. That might sound like arrays, but tuples are different:

1. You can’t add or remove items from a tuple; they are fixed in size.
2. You can’t change the type of items in a tuple; they always have the same types they were created with.
3. You can access items in a tuple using numerical positions or by naming them, but Swift won’t let you read numbers or names that don’t exist.

Tuples are created by placing multiple items into parentheses, like this:

```
var name = (first: "Taylor", last: "Swift")
```

ou then access items using numerical positions starting from 0, or you can access items using their names:

```
name.0
name.first
```

Remember, you can change the values inside a tuple after you create it, but not the types of values. So, if you tried to change **name** to be **(first: "Justin", age: 25)** you would get an error.

### Arrays vs sets vs tuples

Arrays, sets, and tuples can seem similar at first, but they have distinct uses. To help you know which to use, here are some rules.

If you need a specific, fixed collection of related values where each item has a precise position or name, you should use a tuple:

```
let address = (house: 555, street: "Taylor Swift Avenue", city: "Nashville")
```

If you need a collection of values that must be unique or you need to be able to check whether a specific item is in there extremely quickly, you should use a set:

```
let set = Set(["aardvark", "astronaut", "azalea"])
```

If you need a collection of values that can contain duplicates, or the order of your items matters, you should use an array:

```
let pythons = ["Eric", "Graham", "John", "Michael", "Terry", "Terry"]
```

### Dictionaries

Dictionaries are collections of values just like arrays, but rather than storing things with an integer position you can access them using anything you want.

For example, we could create a dictionary that stores the height of singers using their name:

```
let heights = [
    "Taylor Swift": 1.78,
    "Ed Sheeran": 1.73
]
```

We use a colon to separate the value you want to store (e.g. 1.78) from the identifier you want to store it under (e.g. "Taylor Swift").

These identifiers are called *keys*, and you can use them to read data back out of the dictionary:

```
heights["Taylor Swift"]
```

Note: When using type annotations, dictionaries are written in brackets with a colon between your identifier and value types. For example, **[String: Double]** and **[String: String]**.

### Dictionary default values

If you try to read a value from a dictionary using a key that doesn’t exist, Swift will send you back nil – nothing at all. While this might be what you want, there’s an alternative: we can provide the dictionary with a default value to use if we request a missing key.

To demonstrate this, let’s create a dictionary of favorite ice creams for two people:

```
let favoriteIceCream = [
    "Paul": "Chocolate",
    "Sophie": "Vanilla"
]
```

We can read Paul’s favorite ice cream. But if we tried reading the favorite ice cream for Charlotte, we’d get back nil, meaning that Swift doesn’t have a value for that key:

```
favoriteIceCream["Paul"]
favoriteIceCream["Charlotte"]
```

We can fix this by giving the dictionary a default value of "Unknown", so that when no ice cream is found for Charlotte we get back "Unknown" rather than nil:

```
favoriteIceCream["Charlotte", default: "Unknown"]
```

### Creating empty collections

Arrays, sets, and dictionaries are called collections, because they collect values together in one place.

If you want to create an empty collection just write its type followed by opening and closing parentheses. For example, we can create an empty dictionary with strings for keys and values like this:

```
var teams = [String: String]()
```

Similarly, you can create an empty array to store integers like this:

```
var results = [Int]()
```

The exception is creating an empty set, which is done differently:

```
var words = Set<String>()
var numbers = Set<Int>()
```

*This is because Swift has special syntax only for dictionaries and arrays;* other types must use angle bracket syntax like sets.

If you wanted, you could create arrays and dictionaries with similar syntax:

```
var scores = Dictionary<String, Int>()
var results = Array<Int>()
```

### Enumerations

Enumerations – usually called just enums – are a way of defining groups of related values in a way that makes them easier to use.

For example, if you wanted to write some code to represent the success or failure of some work you were doing.

With enums we can define a **Result** type that can be either **success** or **failure**, like this:

```
enum Result {
    case success
    case failure
}
```

And now when we use it we must choose one of those two values:

```
let result = Result.failure
```

### Enum associated values

As well as storing a simple value, enums can also store associated values attached to each case. This lets you attach additional information to your enums so they can represent more nuanced data.

For example, we might define an enum that stores various kinds of activities. Enum associated values let us add additional details:

```
enum Activity {
    case bored
    case running(destination: String)
    case talking(topic: String)
    case singing(volume: Int)
}
```

Now we can be more precise – we can say that someone is talking about football:

```
let talking = Activity.talking(topic: "football")
```

### Enum raw values

Sometimes you need to be able to assign values to enums so they have meaning. This lets you create them dynamically, and also use them in different ways.

For example, you might create a **Planet** enum that stores integer values for each of its cases:

```
enum Planet: Int {
    case mercury
    case venus
    case earth
    case mars
}
```

Swift will automatically assign each of those a number starting from 0, and you can use that number to create an instance of the appropriate enum case. For example, **earth** will be given the number 2, so you can write this:

```
let earth = Planet(rawValue: 2)
```

If you want, you can assign one or more cases a specific value, and Swift will generate the rest. It’s not very natural for us to think of Earth as the second planet, so you could write this:

```
enum Planet: Int {
    case mercury = 1
    case venus
    case earth
    case mars
}
```

Now Swift will assign 1 to **mercury** and count upwards from there, meaning that **earth** is now the third planet.

## Operators and conditions
