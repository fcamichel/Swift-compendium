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
  * [Arithmetic operators](#arithmetic-operators)
  * [Operator overloading](#operator-overloading)
  * [Compound assignment operators](#compound-assignment-operators)
  * [Comparison operators](#comparison-operators)
  * [Conditions](#conditions)
  * [Combining conditions](#combining-conditions)
  * [The ternary operator](#the-ternary-operator)
  * [Switch statements](#switch-statements)
  * [Range operators](#range-operators)
- [Looping](#looping)
  * [For loops](#for-loops)
  * [While loops](#while-loops)
  * [Repeat loops](#repeat-loops)
  * [Exiting loops](#exiting-loops)
  * [Exiting multiple loops](#exiting-multiple-loops)
  * [Skipping items](#skipping-items)
  * [Infinite loops](#infinite-loops)
- [Functions](#functions)
  * [Writing functions](#writing-functions)
  * [Accepting parameters](#accepting-parameters)
  * [Returning values](#returning-values)
  * [Parameter labels](#parameter-labels)
  * [Omitting parameter labels](#omitting-parameter-labels)
  * [Default parameters](#default-parameters)
  * [Variadic functions](#variadic-functions)
  * [Writing throwing functions](#writing-throwing-functions)
  * [Running throwing functions](#running-throwing-functions)
  * [inout parameters](#inout-parameters)
- [Closures](#closures)
  * [Creating basic closures](#creating-basic-closures)
  * [Accepting parameters in a closure](#accepting-parameters-in-a-closure)
  * [Returning values from a closure](#returning-values-from-a-closure)
  * [Closures as parameters](#closures-as-parameters)
  * [Trailing closure syntax](#trailing-closure-syntax)
  * [Using closures as parameters when they accept parameters](#using-closures-as-parameters-when-they-accept-parameters)
  * [Using closures as parameters when they return values](#using-closures-as-parameters-when-they-return-values)
  * [Shorthand parameter names](#shorthand-parameter-names)
  * [Closures with multiple parameters](#closures-with-multiple-parameters)
  * [Returning closures from functions](#returning-closures-from-functions)
  * [Capturing values](#capturing-values)

## Simple types

### Variables

```swift
var str = "Hello, playground"
```

That creates a new variable called **str**, giving it the value "Hello, playground".

Because **str** is a variable we can change it:

```swift
str = "Goodbye"
```

We don’t need **var** the second time because the variable has already been created – we’re just changing it.

### Strings and integers

Swift is what’s known as a type-safe language, which means that every variable must be of one specific type. 

```swift
var age = 38
```

That holds a whole number, so Swift assigns the type **Int** – short for "integer".

If you have large numbers, Swift lets you use underscores as thousands separators – they don’t change the number, but they do make it easier to read. For example:

```swift
var population = 8_000_000
```

Strings and integers are different types, and they can’t be mixed. So, while it’s safe to change **str** to "Goodbye", I can’t make it 38 because that’s an **Int** not a **String**.

### Multi-line strings

Standard Swift strings use double quotes, but you can’t include line breaks in there.

If you want multi-line strings you need slightly different syntax: start and end with three double quote marks, like this:

```swift
var str1 = """
This goes
over multiple
lines
"""
```

Swift is very particular about how you write those quote marks: the opening and closing triple must be on their own line, but opening and closing line breaks won’t be included in your final string.

If you only want multi-line strings to format your code neatly, and you don’t want those line breaks to actually be in your string, end each line with a **\\**, like this:

```swift
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

```swift
var pi = 3.141
```

Doubles are different from integers, and you can’t mix them by accident.

As for booleans, they are much simpler: they just hold either true or false, and Swift will automatically assign the boolean type to any variable assigned either true or false as its value.

For example:

```swift
var awesome = true
```

### String interpolation

You can place any type of variable inside your string – all you have to do is write a backslash, **\\**, followed by your variable name in parentheses. For example:

```swift
var score = 85
var str = "Your score was \(score)"
```

You can do this as many times as you need, making strings out of strings if you want:

```swift
var results = "The test results are here: \(str)"
```

String interpolation isn’t just limited to placing variables – you can actually run code inside there.

### Constants

Very often you want to set a value once and never change it, and so we have an alternative to the var keyword called **let**.

The **let** keyword creates constants, which are values that can be set once and never again. For example:

```swift
let taylor = "swift"
```

You should always use **let** unless you specifically want to change a value.

### Type annotations

Swift assigns each variable and constant a type based on what value it’s given when it’s created.

If you want you can be explicit about the type of your data rather than relying on Swift’s type inference, like this:

```swift
let album: String = "Reputation"
let year: Int = 1989
let height: Double = 1.78
let taylorRocks: Bool = true
```

## Complex Types

### Arrays

Arrays are collections of values that are stored as a single value. For example, John, Paul, George, and Ringo are names, but arrays let you group them in a single value called The Beatles.

In code, we write this:

```swift
let john = "John Lennon"
let paul = "Paul McCartney"
let george = "George Harrison"
let ringo = "Ringo Starr"

let beatles = [john, paul, george, ringo]
```

That last line makes the array: it starts and ends with brackets, with each item in the array separated by a comma.

You can read values from an array by writing a number inside brackets. Array positions count from 0, so if you want to read "Paul McCartney" you would write this:

```swift
beatles[1]
```

Be careful: Swift crashes if you read an item that doesn’t exist. For example, trying to read **beatles[9]** is a bad idea.

Note: If you’re using type annotations, arrays are written in brackets: **[String]**, **[Int]**, **[Double]**, and **[Bool]**.

```swift
var scores: [Int] = [10, 12, 9]
```

### Sets

Sets are collections of values just like arrays, except they have two differences:

1. Items aren’t stored in any order; they are stored in what is effectively a random order.
2. No item can appear twice in a set; all items must be unique.

You can create sets directly from arrays, like this:

```swift
let colors = Set(["red", "green", "blue"])
```

Because they are unordered, you can’t read values from a set using numerical positions like you can with arrays.

If you try to insert a duplicate item into a set, the duplicates get ignored. For example:

```swift
let colors2 = Set(["red", "green", "blue", "red", "blue"])
```

The final colors2 set will still only include red, green, and blue once.

### Tuples

Tuples allow you to store several values together in a single value. That might sound like arrays, but tuples are different:

1. You can’t add or remove items from a tuple; they are fixed in size.
2. You can’t change the type of items in a tuple; they always have the same types they were created with.
3. You can access items in a tuple using numerical positions or by naming them, but Swift won’t let you read numbers or names that don’t exist.

Tuples are created by placing multiple items into parentheses, like this:

```swift
var name = (first: "Taylor", last: "Swift")
```

ou then access items using numerical positions starting from 0, or you can access items using their names:

```swift
name.0
name.first
```

Remember, you can change the values inside a tuple after you create it, but not the types of values. So, if you tried to change **name** to be **(first: "Justin", age: 25)** you would get an error.

### Arrays vs sets vs tuples

Arrays, sets, and tuples can seem similar at first, but they have distinct uses. To help you know which to use, here are some rules.

If you need a specific, fixed collection of related values where each item has a precise position or name, you should use a tuple:

```swift
let address = (house: 555, street: "Taylor Swift Avenue", city: "Nashville")
```

If you need a collection of values that must be unique or you need to be able to check whether a specific item is in there extremely quickly, you should use a set:

```swift
let set = Set(["aardvark", "astronaut", "azalea"])
```

If you need a collection of values that can contain duplicates, or the order of your items matters, you should use an array:

```swift
let pythons = ["Eric", "Graham", "John", "Michael", "Terry", "Terry"]
```

### Dictionaries

Dictionaries are collections of values just like arrays, but rather than storing things with an integer position you can access them using anything you want.

For example, we could create a dictionary that stores the height of singers using their name:

```swift
let heights = [
    "Taylor Swift": 1.78,
    "Ed Sheeran": 1.73
]
```

We use a colon to separate the value you want to store (e.g. 1.78) from the identifier you want to store it under (e.g. "Taylor Swift").

These identifiers are called *keys*, and you can use them to read data back out of the dictionary:

```swift
heights["Taylor Swift"]
```

Note: When using type annotations, dictionaries are written in brackets with a colon between your identifier and value types. For example, **[String: Double]** and **[String: String]**.

### Dictionary default values

If you try to read a value from a dictionary using a key that doesn’t exist, Swift will send you back nil – nothing at all. While this might be what you want, there’s an alternative: we can provide the dictionary with a default value to use if we request a missing key.

To demonstrate this, let’s create a dictionary of favorite ice creams for two people:

```swift
let favoriteIceCream = [
    "Paul": "Chocolate",
    "Sophie": "Vanilla"
]
```

We can read Paul’s favorite ice cream. But if we tried reading the favorite ice cream for Charlotte, we’d get back nil, meaning that Swift doesn’t have a value for that key:

```swift
favoriteIceCream["Paul"]
favoriteIceCream["Charlotte"]
```

We can fix this by giving the dictionary a default value of "Unknown", so that when no ice cream is found for Charlotte we get back "Unknown" rather than nil:

```swift
favoriteIceCream["Charlotte", default: "Unknown"]
```

### Creating empty collections

Arrays, sets, and dictionaries are called collections, because they collect values together in one place.

If you want to create an empty collection just write its type followed by opening and closing parentheses. For example, we can create an empty dictionary with strings for keys and values like this:

```swift
var teams = [String: String]()
```

Similarly, you can create an empty array to store integers like this:

```swift
var results = [Int]()
```

The exception is creating an empty set, which is done differently:

```swift
var words = Set<String>()
var numbers = Set<Int>()
```

*This is because Swift has special syntax only for dictionaries and arrays;* other types must use angle bracket syntax like sets.

If you wanted, you could create arrays and dictionaries with similar syntax:

```swift
var scores = Dictionary<String, Int>()
var results = Array<Int>()
```

### Enumerations

Enumerations – usually called just enums – are a way of defining groups of related values in a way that makes them easier to use.

For example, if you wanted to write some code to represent the success or failure of some work you were doing.

With enums we can define a **Result** type that can be either **success** or **failure**, like this:

```swift
enum Result {
    case success
    case failure
}
```

And now when we use it we must choose one of those two values:

```swift
let result = Result.failure
```

### Enum associated values

As well as storing a simple value, enums can also store associated values attached to each case. This lets you attach additional information to your enums so they can represent more nuanced data.

For example, we might define an enum that stores various kinds of activities. Enum associated values let us add additional details:

```swift
enum Activity {
    case bored
    case running(destination: String)
    case talking(topic: String)
    case singing(volume: Int)
}
```

Now we can be more precise – we can say that someone is talking about football:

```swift
let talking = Activity.talking(topic: "football")
```

### Enum raw values

Sometimes you need to be able to assign values to enums so they have meaning. This lets you create them dynamically, and also use them in different ways.

For example, you might create a **Planet** enum that stores integer values for each of its cases:

```swift
enum Planet: Int {
    case mercury
    case venus
    case earth
    case mars
}
```

Swift will automatically assign each of those a number starting from 0, and you can use that number to create an instance of the appropriate enum case. For example, **earth** will be given the number 2, so you can write this:

```swift
let earth = Planet(rawValue: 2)
```

If you want, you can assign one or more cases a specific value, and Swift will generate the rest. It’s not very natural for us to think of Earth as the second planet, so you could write this:

```swift
enum Planet: Int {
    case mercury = 1
    case venus
    case earth
    case mars
}
```

Now Swift will assign 1 to **mercury** and count upwards from there, meaning that **earth** is now the third planet.

## Operators and conditions


### Arithmetic operators

Operators are those little mathematical symbols like + and -, and Swift has a huge range of them.

We can add and subtract using **+** and **-**:

```swift
let total = firstScore + secondScore
let difference = firstScore - secondScore
```

And we can multiply and divide using **\*** and **/**:

```swift
let product = firstScore * secondScore
let divided = firstScore / secondScore
```

Swift has a special operator for calculating remainders after division: **%**. It calculates how many times one number can fit inside another, then sends back the value that’s left over.

### Operator overloading

Swift supports operator overloading, which is a fancy way of saying that what an operator does depends on the values you use it with. For example, **+** sums integers like this:

```swift
let meaningOfLife = 42
let doubleMeaning = 42 + 42
```

But **+** also joins strings, like this:

```swift
let fakers = "Fakers gonna "
let action = fakers + "fake"
```

You can even use **+** to join arrays, like this:

```swift
let firstHalf = ["John", "Paul"]
let secondHalf = ["George", "Ringo"]
let beatles = firstHalf + secondHalf
```

Remember, Swift is a type-safe language, which means it won’t let you mix types.

### Compound assignment operators

Swift has shorthand operators that combine one operator with an assignment, so you can change a variable in place. These look like the existing operators you know **+**, **-**, **\***, and **/**, but they have an **=** on the end because they assign the result back to whatever variable you were using.

For example, if someone scored 95 in an exam but needs to be penalized 5 points, you could write this:

```swift
var score = 95
score -= 5
```

Similarly, you can add one string to another using **+=**:

```swift
var quote = "The rain in Spain falls mainly on the "
quote += "Spaniards"
```

### Comparison operators

Swift has several operators that perform comparison, and these work more or less like you would expect in mathematics.

here are two operators that check for equality: **==** checks two values are the same, and **!=** (pronounced "not equals") checks two values are not the same:

```swift
firstScore == secondScore
firstScore != secondScore
```

There are four operators for comparing whether one value is greater than, less than, or equal to another. These are just like in mathematics:

```swift
firstScore < secondScore
firstScore >= secondScore
```

Each of these also work with strings, because strings have a natural alphabetical order:

```swift
"Taylor" <= "Swift"
```

### Conditions

Now you know some operators you can write conditions using **if** statements. You give Swift a condition, and if that condition is true it will run code of your choosing.

print(): you run it with some text, and it will be printed out.

We can use conditions to check for a winning Blackjack hand:

```swift
let firstCard = 11
let secondCard = 10

if firstCard + secondCard == 21 {
    print("Blackjack!")
}
```

The code inside the braces – **{** and **}** – will be printed if the condition is true. If you want you can provide alternative code to run if the condition is false, using **else**:

```swift
if firstCard + secondCard == 21 {
    print("Blackjack!")
} else {
    print("Regular cards")
}
```

You can also chain conditions together using **else if**:

```swift
if firstCard + secondCard == 2 {
    print("Aces – lucky!")
} else if firstCard + secondCard == 21 {
    print("Blackjack!")
} else {
    print("Regular cards")
}
```

### Combining conditions

Swift has two special operators that let us combine conditions together: they are **&&** (pronounced "and") and **||** (pronounced "or").

For example, we could check that the age of two people are both over a certain value like this:

```swift
let age1 = 12
let age2 = 21

if age1 > 18 && age2 > 18 {
    print("Both are over 18")
}
```

That **print()** call will only happen if both ages are over 18, which they aren’t. In fact, Swift won’t even bother checking the value of **age2** because it can see that **age1** already failed the test.

The alternative to **&&** is **||**, which evaluates as true if either item passes the test. For example we could print a message if either age is over 18:

```swift
if age1 > 18 || age2 > 18 {
    print("At least one is over 18")
}
```

You can use **&&** and **||** more than once in a single condition, but don’t make things too complicated otherwise it can be hard to read!

### The ternary operator

Swift has a rarely used operator called the ternary operator. It works with three values at once, which is where its name comes from: it checks a condition specified in the first value, and if it’s true returns the second value, but if it’s false returns the third value.

The ternary operator is a condition plus true or false blocks all in one, split up by a question mark and a colon, all of which which makes it rather hard to read. Here’s an example:

```swift
let firstCard = 11
let secondCard = 10
print(firstCard == secondCard ? "Cards are the same" : "Cards are different")
```

That checks whether the two cards are the same, then prints "Cards are the same" if the condition is true, or "Cards are different" if it’s false. We could write the same code using a regular condition:

```swift
if firstCard == secondCard {
    print("Cards are the same")
} else {
    print("Cards are different")
}
```

### Switch statements

If you have several conditions using **if** and **else if**, it’s often clearer to use a different construct known as **switch case**. Using this approach you write your condition once, then list all possible outcomes and what should happen for each of them.

To try this out, here’s a weather constant containing the string **sunny**:

```swift
let weather = "sunny"
```

We can use a **switch** block to print one of four different messages:

```swift
switch weather {
case "rain":
    print("Bring an umbrella")
case "snow":
    print("Wrap up warm")
case "sunny":
    print("Wear sunscreen")
default:
    print("Enjoy your day!")
}
```

In that example, the last case – **default** – is required because Swift makes sure you cover all possible cases so that no eventuality is missed off. If the weather is anything other than rain, snow, or sun, the **default** case will be run.

Swift will only run the code inside each case. If you want execution to continue on to the next case, use the **fallthrough** keyword like this:

```swift
switch weather {
case "rain":
    print("Bring an umbrella")
case "snow":
    print("Wrap up warm")
case "sunny":
    print("Wear sunscreen")
    fallthrough
default:
    print("Enjoy your day!")
}
```

### Range operators

Swift gives us two ways of making ranges: the **..<** and **...** operators. The half-open range operator, **..<**, creates ranges up to but excluding the final value, and the closed range operator, **...**, creates ranges up to and including the final value.

For example, the range **1..<5** contains the numbers 1, 2, 3, and 4, whereas the range **1...5** contains the numbers 1, 2, 3, 4, and 5.

Ranges are helpful with **switch** blocks, because you can use them for each of your cases. For example, if someone sat an exam we could print different messages depending on their score:

```swift
let score = 85

switch score {
case 0..<50:
    print("You failed badly.")
case 50..<85:
    print("You did OK.")
default:
    print("You did great!")
}
```

As before, the **default** case must be there to ensure all possible values are covered.

## Looping

### For loops

Swift has a few ways of writing loops, but their underlying mechanism is the same: run some code repeatedly until a condition evaluates as false.

The most common loop in Swift is a **for** loop: it will loop over arrays and ranges, and each time the loop goes around it will pull out one item and assign to a constant.

For example, here’s a range of numbers:

```swift
let count = 1...10
```

We can use a **for** loop to print each item like this:

```swift
for number in count {
    print("Number is \(number)")
}
```

We can do the same with arrays:

```swift
let albums = ["Red", "1989", "Reputation"]

for album in albums {
    print("\(album) is on Apple Music")
}
```

If you don’t use the constant that **for** loops give you, you should use an underscore instead so that Swift doesn’t create needless values:

```swift
print("Players gonna ")

for _ in 1...5 {
    print("play")
}
```

### While loops

A second way of writing loops is using **while**: give it a condition to check, and its loop code will go around and around until the condition fails.

For example, we could use a **while** loop to simulate a child counting in a game of hide and seek: we start at one, count up to and including 20 while printing each number out, then after the loop print "Ready or not".

Here’s how that looks in Swift:

```swift
var number = 1

while number <= 20 {
    print(number)
    number += 1
}

print("Ready or not, here I come!")
```

### Repeat loops

The third way of writing loops is not commonly used, but it’s so simple to learn we might as well cover it: it’s called the **repeat** loop, and it’s identical to a **while** loop except the condition to check comes at the end.

So, we could rewrite our hide and seek example like this:

```swift
var number = 1

repeat {
    print(number)
    number += 1
} while number <= 20

print("Ready or not, here I come!")
```

Because the condition comes at the end of the **repeat** loop the code inside the loop will always be executed at least once, whereas **while** loops check their condition before their first run.

For example, this **print()** function will never be run, because **false** is always false:

```swift
while false {
    print("This is false")
}
```

Xcode will even warn us that the **print()** line will never be executed.

On the other hand, this **print()** function will be run once, because **repeat** only fails the condition after the loop runs:

```swift
repeat {
    print("This is false")
} while false
```

### Exiting loops

You can exit a loop at any time using the **break** keyword. To try this out, let’s start with a regular **while** loop that counts down for a rocket launch:

```swift
var countDown = 10

while countDown >= 0 {
    print(countDown)
    countDown -= 1
}

print("Blast off!")
```

In this case, the astronaut in command gets bored part-way through the countdown and decides to skip the remainder and launch straight away:

```swift
while countDown >= 0 {
    print(countDown)

    if countDown == 4 {
        print("I'm bored. Let's go now!")
        break
    }

    countDown -= 1
}
```

With that change, as soon as **countDown** reaches 4 the astronaut’s message will be printed, and the rest of the loop gets skipped.

### Exiting multiple loops

If you put a loop inside a loop it’s called a nested loop, and it’s not uncommon to want to break out of both the inner loop and the outer loop at the same time.

As an example, we could write some code to calculate the times tables from 1 through 10 like this:

```swift
for i in 1...10 {
    for j in 1...10 {
        let product = i * j
        print ("\(i) * \(j) is \(product)")
    }
}
```

If we wanted to exit part-way through we need to do two things. First, we give the outside loop a label, like this:

```swift
outerLoop: for i in 1...10 {
    for j in 1...10 {
        let product = i * j
        print ("\(i) * \(j) is \(product)")
    }
}
```

Second, add our condition inside the inner loop, then use **break outerLoop** to exit both loops at the same time:

```swift
outerLoop: for i in 1...10 {
    for j in 1...10 {
        let product = i * j
        print ("\(i) * \(j) is \(product)")

        if product == 50 {
            print("It's a bullseye!")
            break outerLoop
        }
    }
}
```

With a regular **break**, only the inner loop would be exited – the outer loop would continue where it left off.

### Skipping items

As you’ve seen, the **break** keyword exits a loop. But if you just want to skip the current item and continue on to the next one, you should use **continue** instead.

To try this out, we can write a loop from 1 through 10, then use Swift’s remainder operator to skip any numbers that are odd:

```swift
for i in 1...10 {
    if i % 2 == 1 {
        continue
    }

    print(i)
}
```

Remember, the remainder operator figures out how many times 2 fits into each number in our loop, then returns whatever is left over. So, if 1 is left over, it means the number is odd, so we can use **continue** to skip it.

### Infinite loops

It’s common to use **while** loops to make *infinite* loops: loops that either have no end or only end when you’re ready. All apps on your iPhone use infinite loops, because they start running, then continually watch for events until you choose to quit them.

To make an infinite loop, just use **true** as your condition. **true** is always true, so the loop will repeat forever. _Warning:_ Please make sure you have a check that exits your loop, otherwise it will never end.

As an example, we’re going to use **while true** to print the music of John Cage’s piece 4’33” – if you didn’t know, it’s famous because it’s 4 minutes and 33 seconds of complete silence.

We can write the "music" for this piece using **while true**, with a condition that exits the loop when we’ve gone around enough times:

```swift
var counter = 0

while true {
    print(" ")
    counter += 1

    if counter == 273 {
        break
    }
}
```

## Functions

### Writing functions

Functions let us re-use code, which means we can write a function to do something interesting then run that function from lots of places. Repeating code is generally a bad idea, and functions help us avoid doing that.

To start with, we’re going to write a function that prints help information for users of our app. We might need this anywhere in our app, so having it as a function is a good idea.

Swift functions start with the **func** keyword, then your function name, then open and close parentheses. All the body of your function – the code that should be run when the function is requested – is placed inside braces.

Let’s write the **printHelp()** function now:

```swift
func printHelp() {
    let message = """
Welcome to MyApp!

Run this app inside a directory of images and
MyApp will resize them all into thumbnails
"""

    print(message)
}
```

We can now run that using **printHelp()** by itself:

```swift
printHelp()
```

Running a function is often referred to as calling a function.

### Accepting parameters

Functions become more powerful when they can be customized each time you run them. Swift lets you send values to a function that can then be used inside the function to change the way it behaves. We’ve used this already – we’ve been sending strings and integers to the **print()** function, like this:

```swift
print("Hello, world!")
```

Values sent into functions this way are called parameters.

To make your own functions accept parameters, give each parameter a name, then a colon, then tell Swift the type of data it must be. All this goes inside the parentheses after your function name.

For example, we can write a function to print the square of any number:

```swift
func square(number: Int) {
    print(number * number)
}
```

That tells Swift we expect to receive an **Int**, and it should be called **number**. This name is used both inside the function when you want to refer to the parameter, but also when you run the function, like this:

```swift
square(number: 8)
```

### Returning values

As well as receiving data, functions can also send back data. To do this, write a dash then a right angle bracket after your function’s parameter list, then tell Swift what kind of data will be returned.

Inside your function, you use the **return** keyword to send a value back if you have one. Your function then immediately exits, sending back that value – no other code from that function will be run.

We could rewrite our **square()** function to return a value rather than print it directly:

```swift
func square(number: Int) -> Int {
    return number * number
}
```

Now we can grab that return value when the function is run, and print it there:

```swift
let result = square(number: 8)
print(result)
```

If you need to return multiple values, this is a perfect example of when to use tuples.

### Parameter labels

We wrote our **square()** function like this:

```swift
func square(number: Int) -> Int {
    return number * number
}
```

That names its parameter **number**, so we can use **number** inside the function to refer to it, but we must also use the name when running the function, like this:

```swift
let result = square(number: 8)
```

Swift lets us provide two names for each parameter: one to be used externally when calling the function, and one to be used internally inside the function. This is as simple as writing two names, separated by a space.

To demonstrate this, here’s a function that uses two names for its string parameter:

```swift
func sayHello(to name: String) {
    print("Hello, \(name)!")
}
```

The parameter is called **to name**, which means externally it’s called **to**, but internally it’s called **name**. This gives variables a sensible name inside the function, but means calling the function reads naturally:

```swift
sayHello(to: "Taylor")
```

### Omitting parameter labels

You might have noticed that we don’t actually send any parameter names when we call **print()** – we say **print("Hello")** rather than **print(message: "Hello")**.

You can get this same behavior in your own functions by using an underscore, **_**, for your external parameter name, like this:

```swift
func greet(_ person: String) {
    print("Hello, \(person)!")
}
```

You can now call **greet()** without having to use the **person** parameter name:

```swift
greet("Taylor")
```

This can make some code more natural to read, but generally it’s better to give your parameters external names to avoid confusion. For example, if I say **setAlarm(5)** it’s hard to tell what that means – does it set an alarm for five o’clock, set an alarm for five hours from now, or activate pre-configured alarm number 5?

### Default parameters

The **print()** function prints something to the screen, but always adds a new line to the end of whatever you printed, so that multiple calls to **print()** don’t all appear on the same line.

You can change that behavior if you want, so you could use spaces rather than line breaks. Most of the time, though, folks want new lines, so **print()** has a **terminator** parameter that uses new line as its default value.

You can give your own parameters a default value just by writing an **=** after its type followed by the default you want to give it. So, we could write a **greet()** function that can optionally print nice greetings:

```swift
func greet(_ person: String, nicely: Bool = true) {
    if nicely == true {
        print("Hello, \(person)!")
    } else {
        print("Oh no, it's \(person) again...")
    }
}
```

That can be called in two ways:

```swift
greet("Taylor")
greet("Taylor", nicely: false)
```

### Variadic functions

Some functions are variadic, which is a fancy way of saying they accept any number of parameters of the same type. The **print()** function is actually variadic: if you pass lots of parameters, they are all printed on one line with spaces between them:

```swift
print("Haters", "gonna", "hate")
```

You can make any parameter variadic by writing ... after its type. So, an **Int** parameter is a single integer, whereas **Int...** is zero or more integers – potentially hundreds.

Inside the function, Swift converts the values that were passed in to an array of integers, so you can loop over them as needed.

To try this out, let’s write a **square()** function that can square many numbers:

```swift
func square(numbers: Int...) {
    for number in numbers {
        print("\(number) squared is \(number * number)")
    }
}
```

Now we can run that with lots of numbers just by passing them in separated by commas:

```swift
square(numbers: 1, 2, 3, 4, 5)
```

### Writing throwing functions

Sometimes functions fail because they have bad input, or because something went wrong internally. Swift lets us throw errors from functions by marking them as **throws** before their return type, then using the **throw** keyword when something goes wrong.

First we need to define an **enum** that describes the errors we can throw. These must always be based on Swift’s existing **Error** type. We’re going to write a function that checks whether a password is good, so we’ll throw an error if the user tries an obvious password:

```swift
enum PasswordError: Error {
    case obvious
}
```

Now we’ll write a **checkPassword()** function that will throw that error if something goes wrong. This means using the **throws** keyword before the function’s return value, then using throw **PasswordError.obvious** if their password is "password".

Here’s that in Swift:

```swift
func checkPassword(_ password: String) throws -> Bool {
    if password == "password" {
        throw PasswordError.obvious
    }

    return true
}
```

### Running throwing functions

Swift doesn’t like errors to happen when your program runs, which means it won’t let you run an error-throwing function by accident.

Instead, you need to call these functions using three new keywords: **do** starts a section of code that might cause problems, **try** is used before every function that might throw an error, and **catch** lets you handle errors gracefully.

If any errors are thrown inside the **do** block, execution immediately jumps to the **catch** block. Let’s try calling **checkPassword()** with a parameter that throws an error:

```swift
do {
    try checkPassword("password")
    print("That password is good!")
} catch {
    print("You can't use that password.")
}
```

When that code runs, "You can’t use that password" is printed, but "That password is good" won’t be – that code will never be reached, because the error is thrown.

### inout parameters

All parameters passed into a Swift function are constants, so you can’t change them. If you want, you can pass in one or more parameters as **inout**, which means they can be changed inside your function, and those changes reflect in the original value outside the function.

For example, if you want to double a number in place – i.e., change the value directly rather than returning a new one – you might write a function like this:

```swift
func doubleInPlace(number: inout Int) {
    number *= 2
}
```

To use that, you first need to make a variable integer – you can’t use constant integers with **inout**, because they might be changed. You also need to pass the parameter to **doubleInPlace** using an ampersand, **&**, before its name, which is an explicit recognition that you’re aware it is being used as **inout**.

In code, you’d write this:

```swift
var myNum = 10 
doubleInPlace(number: &myNum)
```

## Closures

### Creating basic closures

Swift lets us use functions just like any other type such as strings and integers. This means you can create a function and assign it to a variable, call that function using that variable, and even pass that function into other functions as parameters.

Functions used in this way are called *closures*, and although they work like functions they are written a little differently.

Let’s start with a simple example that prints a message:

```swift
let driving = {
    print("I'm driving in my car")
}
```

That effectively creates a function without a name, and assigns that function to **driving**. You can now call **driving()** as if it were a regular function, like this:

```swift
driving()
```

### Accepting parameters in a closure

When you create closures, they don’t have a name or space to write any parameters. That doesn’t mean they can’t *accept* parameters, just that they do so in a different way: they are listed *inside* the open braces.

To make a closure accept parameters, list them inside parentheses just after the opening brace, then write **in** so that Swift knows the main body of the closure is starting.

For example, we could make a closure that accepts a place name string as its only parameter like this:

```swift
let driving = { (place: String) in
    print("I'm going to \(place) in my car")
}
```

One of the differences between functions and closures is that you don’t use parameter labels when running closures. So, to call driving() now we’d write this:

```swift
driving("London")
```

### Returning values from a closure

Closures can also return values, and they are written similarly to parameters: you write them inside your closure, directly before the **in** keyword.

To demonstrate this, we’re going to take our **driving()** closure and make it return its value rather than print it directly. Here’s the original:

```swift
let driving = { (place: String) in
    print("I'm going to \(place) in my car")
}
```

We want a closure that returns a string rather than printing the message directly, so we need to use **-> String** before **in**, then use **return** just like a normal function:

```swift
let drivingWithReturn = { (place: String) -> String in
    return "I'm going to \(place) in my car"
}
```

We can now run that closure and print its return value:

```swift
let message = drivingWithReturn("London")
print(message)
```

### Closures as parameters

Because closures can be used just like strings and integers, you can pass them into functions. The syntax for this can hurt your brain at first, so we’re going to take it slow.

First, here’s our basic **driving()** closure again:

```swift
let driving = {
    print("I'm driving in my car")
}
```

If we wanted to pass that closure into a function so it can be run inside that function, we would specify the parameter type as **() -> Void**. That means "accepts no parameters, and returns **Void**" – Swift’s way of saying "nothing".

So, we can write a **travel()** function that accepts different kinds of traveling actions, and prints a message before and after:

```swift
func travel(action: () -> Void) {
    print("I'm getting ready to go.")
    action()
    print("I arrived!")
}
```

We can now call that using our **driving** closure, like this:

```swift
travel(action: driving)
```

### Trailing closure syntax

If the last parameter to a function is a closure, Swift lets you use special syntax *called trailing closure syntax*. Rather than pass in your closure as a parameter, you pass it directly after the function inside braces.

To demonstrate this, here’s our **travel()** function again. It accepts an **action** closure so that it can be run between two **print()** calls:

```swift
func travel(action: () -> Void) {
    print("I'm getting ready to go.")
    action()
    print("I arrived!")
}
```

Because its last parameter is a closure, we can call **travel()** using trailing closure syntax like this:

```swift
travel() {
    print("I'm driving in my car")
}
```

In fact, because there aren’t any other parameters, we can eliminate the parentheses entirely:

```swift
travel {
    print("I'm driving in my car")
}
```

Trailing closure syntax is extremely common in Swift, so it’s worth getting used to.

### Using closures as parameters when they accept parameters

This is where closures can start to be read a bit like line noise: a closure you pass into a function can also accept its own parameters.

We’ve been using **() -> Void** to mean "accepts no parameters and returns nothing", but you can go ahead and fill the **()** with the types of any parameters that your closure should accept.

To demonstrate this, we can write a **travel()** function that accepts a closure as its only parameter, and that closure in turn accepts a string:

```swift
func travel(action: (String) -> Void) {
    print("I'm getting ready to go.")
    action("London")
    print("I arrived!")
}
```

Now when we call **travel()** using trailing closure syntax, our closure code is required to accept a string:

```swift
travel { (place: String) in
    print("I'm going to \(place) in my car")
}
```

### Using closures as parameters when they return values

We’ve been using **() -> Void** to mean "accepts no parameters and returns nothing", but you can replace that Void with any type of data to force the closure to return a value.

To demonstrate this, we can write a **travel()** function that accepts a closure as its only parameter, and that closure in turn accepts a string and returns a string:

```swift
func travel(action: (String) -> String) {
    print("I'm getting ready to go.")
    let description = action("London")
    print(description)
    print("I arrived!")
}
```

Now when we call **travel()** using trailing closure syntax, our closure code is required to accept a string and return a string:

```swift
travel { (place: String) -> String in
    return "I'm going to \(place) in my car"
}
```

### Shorthand parameter names

We just made a **travel()** function. It accepts one parameter, which is a closure that itself accepts one parameter and returns a string. That closure is then run between two calls to **print()**.

Here’s that in code:

```swift
func travel(action: (String) -> String) {
    print("I'm getting ready to go.")
    let description = action("London")
    print(description)
    print("I arrived!")
}
```

We can call **travel()** using something like this:

```swift
travel { (place: String) -> String in
    return "I'm going to \(place) in my car"
}
```

However, Swift *knows* the parameter to that closure must be a string, so we can remove it:

```swift
travel { place -> String in
    return "I'm going to \(place) in my car"
}
```

It also knows the closure must return a string, so we can remove that. As the closure only has one line of code that must be the one that returns the value, so Swift lets us remove the **return** keyword too:

```swift
travel { place in
    "I'm going to \(place) in my car"
}
```

Swift has a shorthand syntax that lets you go even shorter. Rather than writing **place in** we can let Swift provide automatic names for the closure’s parameters. These are named with a dollar sign, then a number counting from 0.

```swift
travel {
    "I'm going to \($0) in my car"
}
```

### Closures with multiple parameters

Just to make sure everything is clear, we’re going to write another closure example using two parameters.

This time our **travel()** function will require a closure that specifies where someone is traveling to, and the speed they are going. This means we need to use **(String, Int) -> String** for the parameter’s type:

```swift
func travel(action: (String, Int) -> String) {
    print("I'm getting ready to go.")
    let description = action("London", 60)
    print(description)
    print("I arrived!")
}
```

We’re going to call that using a trailing closure and shorthand closure parameter names. Because this accepts two parameters, we’ll be getting both **\$0** and **\$1**:

```swift
travel {
    "I'm going to \($0) at \($1) miles per hour."
}
```

Some people prefer not to use shorthand parameter names like **\$0** because it can be confusing, and that’s OK – do whatever works best for you.

### Returning closures from functions

In the same way that you can pass a closure to a function, you can get closures returned *from* a function too.

The syntax for this is a bit confusing a first, because it uses **->** twice: once to specify your function’s return value, and a second time to specify your closure’s return value.

To try this out, we’re going to write a **travel()** function that accepts no parameters, but returns a closure. The closure that gets returned must be called with a string, and will return nothing.

Here’s how that looks in Swift:

```swift
func travel() -> (String) -> Void {
    return {
        print("I'm going to \($0)")
    }
}
```

We can now call **travel()** to get back that closure, then call it as a function:

```swift
let result = travel()
result("London")
```

It’s technically allowable – although really not recommended! – to call the return value from **travel()** directly:

```swift
let result2 = travel()("London")
```

### Capturing values

If you use any external values inside your closure, Swift *captures* them – stores them alongside the closure, so they can be modified even if they don’t exist any more.

Right now we have a **travel()** function that returns a closure, and the returned closure accepts a string as its only parameter and returns nothing:

```swift
func travel() -> (String) -> Void {
    return {
        print("I'm going to \($0)")
    }
}
```

We can call **travel()** to get back the closure, then call that closure freely:

```swift
let result = travel()
result("London")
```

Closure capturing happens if we create values in **travel()** that get used inside the closure. For example, we might want to track how often the returned closure is called:

```swift
func travel() -> (String) -> Void {
    var counter = 1

    return {
        print("\(counter). I'm going to \($0)")
        counter += 1
    }
}
```

Even though that **counter** variable was created inside **travel()**, it gets captured by the closure so it will still remain alive for that closure.

So, if we call **result("London")** multiple times, the counter will go up and up:

```swift
result("London")
result("London")
result("London")
```
