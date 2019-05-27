---
layout: post
title:  "Some Swift tips for beginner and intermediate"
date:   2019-05-23
categories: iOS, developer
comments: true
published: false
---


<div class="message">
"iOS and macOS programs have long been written in a language called Objective-C. In the summer of 2014, Apple introduced a new and exciting language for writing apps called Swift" 
<br><cite></cite>
</div>

<a rel="ar" href="/assets/img/AR-QL-Pictures/retrotv.usdz">
    <img src="/assets/img/AR-QL-Pictures/Screenshot5.jpg">
</a>

SDK is the iOS Software Development Kit. Xcode is a code editor known as an integrated development environment (IDE).  
The iOS SDK is a suite of prebuilt programming libraries that help you write apps quickly and in a way that Apple expects. A programming library is a collection of related software modules that you can use in your programs. 
Next, add an Organization Name. You can invent your own company name, use your real name, or choose anything else you want. The Organization Identifier needs to be a unique name, so it’s common to format this like a backward website address.

The Bundle Identifier combines the names you entered in the Organization Identifier and the Product Name fields, and it is created automatically.

Swift is what’s known as a type-safe language, which means that every variable must be of one specific type

Open Playgrounds to practice your code. Open Xcode and do shift alt command N
command shift Y shows the console window below.
Check playgrounds for ipad too!


When you create a variable and give it an initial value the computer is actually smart enough to figure out the data type, most of the time. This is called type inference!

Casting is a way to temporarily transform the data type of a variable or constant.

This is the syntax

let intNumber = 2
var doubleNumber = Double(intNumber)

In Swift, the spaces around an operator are important, and both variables need to have the same type! 

Foundation framework! 

import Foundation // put it on the top of the playground

> The Foundation framework provides a base layer of functionality for apps and frameworks, including data storage and persistence, text processing, date and time calculations, sorting and filtering, and networking

### Multi-line strings

{% highlight swift %}

/* Standard Swift strings use double quotes, but you can’t include line breaks in there.
If you want multi-line strings you need slightly different syntax: start and end with three double quote marks, like this: */

var str1 = """
This goes
over multiple
lines
"""
/*Swift is very particular about how you write those quote marks: the opening and closing triple must be on their own line, but that opening and closing line breaks won’t be included in your final string.

If you only want multi-line strings to format your code neatly, and you don’t want those line breaks to actually be in your string, end each line with a \, like this:
*/
var str2 = """
This goes \
over multiple \
lines
""" 

{% endhighlight %}

### String interpolation

 Swift also has a feature called string interpolation – the ability to place variables inside your strings to make them more useful.

You can place any type of variable inside your string – all you have to do is write a backslash, \, followed by your variable name in parentheses. For example:

var score = 85
var str = "Your score was \(score)"
As you’ll see later on, string interpolation isn’t just limited to placing variables – you can actually run code inside there.

### Constants
You make variables using var and constants using let. It’s preferable to use constants as often as possible.
The let keyword creates constants, which are values that can be set once and never again.

### Type annotations
If you want you can be explicit about the type of your data rather than relying on Swift’s type inference, like this:

let album: String = "Reputation"
let year: Int = 1989
let height: Double = 1.78
let taylorRocks: Bool = true

### COMPLEX DATA TYPES
Arrays are collections of values that are stored as a single value
Sets are collections of values just like arrays, except they have two differences:  
Items aren’t stored in any order; they are stored in what is effectively a random order.  
No item can appear twice in a set; all items must be unique.  
You can create sets directly from arrays, like this:

let colors = Set(["red", "green", "blue"])
If you try to insert a duplicate item into a set, the duplicates get ignored. For example:

let colors2 = Set(["red", "green", "blue", "red", "blue"])

Tuples allow you to store several values together in a single value. That might sound like arrays, but tuples are different:

You can’t add or remove items from a tuple; they are fixed in size.
You can’t change the type of items in a tuple; they always have the same types they were created with.
You can access items in a tuple using numerical positions or by naming them
Tuples are created by placing multiple items into parentheses, like this:

var name = (first: "Taylor", last: "Swift")
You then access items using numerical positions starting from 0:
name.0
Or you can access items using their names:
name.first

If you need a specific, fixed collection of related values where each item has a precise position or name, you should use a tuple:
If you need a collection of values that must be unique or you need to be able to check whether a specific item is in there extremely quickly, you should use a set:
If you need a collection of values that can contain duplicates, or the order of your items matters, you should use an array:
Dictionaries are collections of values just like arrays, but rather than storing things with an integer position you can access them using anything you want.

When using type annotations, dictionaries are written in brackets with a colon between your identifier and value types. For example, [String: Double] and [String: String].

### Dictionary default values

let favoriteIceCream = [
    "Paul": "Chocolate",
    "Sophie": "Vanilla"
]
favoriteIceCream["Charlotte", default: "Unknown"]

### Creating empty collections
Arrays, sets, and dictionaries are called collections

var teams = [String: String]()

var results = [Int]()

The exception is creating an empty set, which is done differently:
var words = Set<String>()
var numbers = Set<Int>()
Swift has special syntax only for dictionaries and arrays; other types must use angle bracket syntax like sets.

### Enumerations

enum Result {
    case success
    case failure
}
And now when we use it we must choose one of those two values:

let result4 = Result.failure

### Enum associated values

Enum raw values
If you want, you can assign one or more cases a specific value, and Swift will generate the rest. It’s not very natural for us to think of Earth as the second planet, so you could write this:

enum Planet: Int {
    case mercury = 1
    case venus
    case earth
    case mars
}
Now Swift will assign 1 to mercury and count upwards from there, meaning that earth is now the third planet.

### Operator overloading
For example, + sums integers But + also joins strings and even arrays

### The ternary operator
Swift has a rarely used operator called the ternary operator.
let firstCard = 11
let secondCard = 10
print(firstCard == secondCard ? "Cards are the same" : "Cards are different")

### Switch statements
Swift gives us two ways of making ranges: the ..< and ... operators. The half-open range operator, ..<, creates ranges up to but excluding the final value, and the closed range operator, ..., creates ranges up to and including the final value.
the default case must be there to ensure all possible values are covered.

### 

### Sources:

[Integrating Apps and Content with AR Quick Look - developer.apple.com](https://developer.apple.com/videos/play/wwdc2018/603/)
<hr>

[^1]: What?