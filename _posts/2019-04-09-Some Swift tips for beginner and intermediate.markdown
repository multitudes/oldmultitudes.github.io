---
layout: post
title:  "Some Swift for beginner and intermediate"
date:   2019-04-23
categories: iOS, developer
comments: true
published: true
---


<div class="message">
"iOS and macOS programs have long been written in a language called Objective-C. In the summer of 2014, Apple introduced a new and exciting language for writing apps called Swift" 
<br><cite></cite>
</div>

I just finished the 100 Days of Swift by Paul Hudson and needed a place to put down some notes for my learning and enjoyment :)
This post is inspired from the 100 Days of Swift [days 1 to 12](https://www.hackingwithswift.com/100):



<!-- <a rel="ar" href="/assets/img/AR-QL-Pictures/retrotv.usdz">
    <img src="/assets/img/AR-QL-Pictures/Screenshot5.jpg">
</a> -->

### About the Apple SDK

SDK is the iOS Software Development Kit.  
The iOS SDK is a suite of prebuilt programming libraries that help you write apps quickly and in a way that Apple expects. A programming library is a collection of related software modules that you can use in your programs.  
Xcode is a code editor known as an integrated development environment (IDE).    

### Settings
 
Some of the things Xcode will ask you:  
* "Organization Identifier" is a unique identifier usually made up of your personal web site domain name in reverse, can be anything as long as it is unique 
* The "Organization Name", here you can invent your own company name, use your real name, or choose anything else you want.   
* The "Bundle Identifier" combines the names you entered in the Organization Identifier and the Product Name fields, and it is created automatically.  


### Open the Swift playgrounds

Swift is what’s known as a type-safe language, which means that every variable must be of one specific type  

Open Playgrounds to practice your code. Open Xcode and do `shift` +`alt`+ `command`+ `N`  to create a new playground.

`command` + `shift` `Y` shows the console window below.  

PS. Check playgrounds for ipad too!

Put this line on the top of the playground
```
import Foundation  
```
> The Foundation framework provides a base layer of functionality for apps and frameworks, including data storage and persistence, text processing, date and time calculations, sorting and filtering, and networking

### Casting

When you create a variable and give it an initial value the computer is actually smart enough to figure out the data type, most of the time. This is called type inference!

Casting is a way to temporarily transform the data type of a variable or constant.

This is the syntax
``` swift
let intNumber = 2
var doubleNumber = Double(intNumber)
```
In Swift, the spaces around an operator are important, and both variables need to have the same type! 

### Multi-line strings

/* Standard Swift strings use double quotes, but you can’t include line breaks in there.
If you want multi-line strings you need slightly different syntax: start and end with three double quote marks, like this: 
``` swift
var str1 = """
This goes
over multiple
lines
"""
```
Swift is very particular about how you write those quote marks: the opening and closing triple must be on their own line, but that opening and closing line breaks won’t be included in your final string.

If you only want multi-line strings to format your code neatly, and you don’t want those line breaks to actually be in your string, end each line with a \, like this:

``` swift
var str2 = """
This goes \
over multiple \
lines
""" 
```
### String interpolation

Swift also has a feature called string interpolation – the ability to place variables inside your strings to make them more useful.

You can place any type of variable inside your string – all you have to do is write a backslash, \, followed by your variable name in parentheses. For example:

``` swift
var score = 85
var str = "Your score was \(score)"
```
As you’ll see later on, string interpolation isn’t just limited to placing variables – you can actually run code inside there.

### Constants
You make variables using var and constants using let. It’s preferable to use constants as often as possible.
The let keyword creates constants, which are values that can be set once and never again.

### Type annotations
If you want you can be explicit about the type of your data rather than relying on Swift’s type inference, like this:

``` swift
let album: String = "Reputation"
let year: Int = 1989
let height: Double = 1.78
let taylorRocks: Bool = true
```
### COMPLEX DATA TYPES
Arrays are collections of values that are stored as a single value
Sets are collections of values just like arrays, except they have two differences:  
Items aren’t stored in any order; they are stored in what is effectively a random order.  
No item can appear twice in a set; all items must be unique.  
You can create sets directly from arrays, like this:

``` swift
let colors = Set(["red", "green", "blue"])
```
If you try to insert a duplicate item into a set, the duplicates get ignored. For example:

``` swift
let colors2 = Set(["red", "green", "blue", "red", "blue"])
```
Tuples allow you to store several values together in a single value. That might sound like arrays, but tuples are different:

You can’t add or remove items from a tuple; they are fixed in size.
You can’t change the type of items in a tuple; they always have the same types they were created with.
You can access items in a tuple using numerical positions or by naming them
Tuples are created by placing multiple items into parentheses, like this:

``` swift
var name = (first: "Taylor", last: "Swift")
// You then access items using numerical positions starting from 0:
name.0
// Or you can access items using their names:
name.first
```
If you need a specific, fixed collection of related values where each item has a precise position or name, you should use a tuple:
If you need a collection of values that must be unique or you need to be able to check whether a specific item is in there extremely quickly, you should use a set:
If you need a collection of values that can contain duplicates, or the order of your items matters, you should use an array:
Dictionaries are collections of values just like arrays, but rather than storing things with an integer position you can access them using anything you want.

There is a big difference, however, in how Swift returns the values from a dictionary. When you access a value at an index of an array, you are simply given the value. When you access a value with a key in a dictionary, you are given an optional.
Removing an item from a dictionary is quite simple; you do so by setting the value to nil. Because the values in dictionaries are returned as optionals, you don’t have to worry about nil causing any problems 

When using type annotations, dictionaries are written in brackets with a colon between your identifier and value types. For example, [String: Double] and [String: String].

#### Dictionary default values

``` swift
let favoriteIceCream = [
    "Paul": "Chocolate",
    "Sophie": "Vanilla"
]
favoriteIceCream["Charlotte", default: "Unknown"]
```
#### Creating empty collections
Arrays, sets, and dictionaries are called collections

``` swift
var teams = [String: String]()

var results = [Int]()
```
The exception is creating an empty set, which is done differently:

``` swift
var words = Set<String>()
var numbers = Set<Int>()
```
Swift has special syntax only for dictionaries and arrays; other types must use angle bracket syntax like sets.

### Enumerations

``` swift
enum Result {
    case success
    case failure
}
```
And now when we use it we must choose one of those two values:

``` swift
let result4 = Result.failure
```

#### Enum associated values

Enum raw values
If you want, you can assign one or more cases a specific value, and Swift will generate the rest. It’s not very natural for us to think of Earth as the second planet, so you could write this:

``` swift
enum Planet: Int {
    case mercury = 1
    case venus
    case earth
    case mars
}
```

Now Swift will assign 1 to mercury and count upwards from there, meaning that earth is now the third planet.

### Operator overloading

For example, + sums integers But + also joins strings and even arrays

### The ternary operator

Swift has a rarely used operator called the ternary operator.

``` swift
let firstCard = 11
let secondCard = 10
print(firstCard == secondCard ? "Cards are the same" : "Cards are different")
```

### Switch statements

Swift gives us two ways of making ranges: the ..< and ... operators. The half-open range operator, ..<, creates ranges up to but excluding the final value, and the closed range operator, ..., creates ranges up to and including the final value.
the default case must be there to ensure all possible values are covered.



### FUNCTIONS

Functions let us wrap up pieces of code so they can be used in lots of places. We can send data into functions to customize how they work, and get back data that tells us the result that was calculated.

Believe it or not, function calls used to be really slow. Steve Johnson, the author of many early coding tools for the Unix operating system, said this:

> “Dennis Ritchie (the creator of the C programming language) encouraged modularity by telling all and sundry that function calls were really, really cheap in C. Everybody started writing small functions and modularizing. Years later we found out that function calls were still expensive, and our code was often spending 50% of its time just calling them. Dennis had lied to us! But it was too late; we were all hooked...”

Swift lets us provide two names for each parameter: one to be used externally when calling the function, and one to be used internally inside the function. This is as simple as writing two names, separated by a space.

To demonstrate this, here’s a function that uses two names for its string parameter:

``` swift
func sayHello(to name: String) {
    print("Hello, \(name)!")
}
```
The parameter is called to name, which means externally it’s called to, but internally it’s called name. This gives variables a sensible name inside the function, but means calling the function reads naturally:

``` swift
sayHello(to: "Taylor")
```

You might have noticed that we don’t actually send any parameter names when we call print() – we say print("Hello") rather than print(message: "Hello").

You can get this same behavior in your own functions by using an underscore, `_`  
The print() function prints something to the screen, but always adds a new line to the end of whatever you printed, so that multiple calls to print() don’t all appear on the same line.print() has a terminator parameter that uses new line as its default value.

#### Variadic functions

they accept any number of parameters of the same type. The print() function is actually variadic: if you pass lots of parameters, they are all printed on one line with spaces between them:
print("Haters", "gonna", "hate")

You can make any parameter variadic by writing ... after its type

``` swift
func square(numbers: Int...) {...}
...
square(numbers: 1, 2, 3, 4, 5)
```
#### Throwing functions

Sometimes functions fail because they have bad input, or because something went wrong internally. Swift lets us throw errors from functions by marking them as throws before their return type, then using the throw keyword when something goes wrong.

First we need to define an enum that describes the errors we can throw. These must always be based on Swift’s existing Error type. We’re going to write a function that checks whether a password is good, so we’ll throw an error if the user tries an obvious password:

``` swift
enum PasswordError: Error {
    case obvious
}
```
Now we’ll write a checkPassword() function that will throw that error if something goes wrong. This means using the throws keyword before the function’s return value, then using throw PasswordError.obvious if their password is “password”.

Here’s that in Swift:

``` swift
func checkPassword(_ password: String) throws -> Bool {
    if password == "password" {
        throw PasswordError.obvious
    }

    return true
}
```

you need to call these functions using three new keywords: do starts a section of code that might cause problems, try is used before every function that might throw an error, and catch lets you handle errors gracefully.

If any errors are thrown inside the do block, execution immediately jumps to the catch block. Let’s try calling checkPassword() with a parameter that throws an error:
``` swift
do {
    try checkPassword("password")
    print("That password is good!")
} catch {
    print("You can't use that password.")
}
```
#### inout parameters

you can pass in one or more parameters as inout, which means they can be changed inside your function, and those changes reflect in the original value outside the function.

For example, if you want to double a number in place – i.e., change the value directly rather than returning a new one – you might write a function like this:

``` swift
func doubleInPlace(number: inout Int) {
    number *= 2
}
```
You also need to pass the parameter to doubleInPlace using an ampersand, &, before its name, which is an explicit recognition that you’re aware it is being used as inout.

In code, you’d write this:
``` swift
var myNum = 10 
doubleInPlace(number: &myNum)
```

### CLOSURES

Swift lets us use functions just like any other type such as strings and integers. This means you can create a function and assign it to a variable, call that function using that variable, and even pass that function into other functions as parameters.

``` swift
let driving = {
    print("I'm driving in my car")
}
```
creates a function without a name, and assigns that function to driving

You can now call driving() as if it were a regular function, like this:

``` swift
driving()
```
To make a closure accept parameters, list them inside parentheses just after the opening brace, then write in so that Swift knows the main body of the closure is starting.

For example, we could make a closure that accepts a place name string as its only parameter like this:
``` swift
let driving = { (place: String) in
    print("I'm going to \(place) in my car")
}
```
One of the differences between functions and closures is that you don’t use parameter labels when running closures. So, to call driving() now we’d write this:
``` swift
driving("London")
```

We want a closure that returns a string rather than printing the message directly, so we need to use -> String before in, then use return just like a normal function:
``` swift
let drivingWithReturn = { (place: String) -> String in
    return "I'm going to \(place) in my car"
}
```
We can now run that closure and print its return value:
``` swift
let message = drivingWithReturn("London")
print(message)
```
#### Closures as function parameters

Because closures can be used just like strings and integers, you can pass them into functions.

First, here’s our basic driving() closure again
``` swift
let driving = {
    print("I'm driving in my car")
}
```
If we wanted to pass that closure into a function so it can be run inside that function, we would specify the parameter type as () -> Void. That means “accepts no parameters, and returns Void” – Swift’s way of saying “nothing”.

So, we can write a travel() function that accepts different kinds of traveling actions, and prints a message before and after:
``` swift
func travel(action: () -> Void) {
    print("I'm getting ready to go.")
    action()
    print("I arrived!")
}
```
We can now call that using our driving closure, like this:
``` swift
travel(action: driving)
```


#### Trailing closure syntax

If the last parameter to a function is a closure, Swift lets you use special syntax called trailing closure syntax. Rather than pass in your closure as a parameter, you pass it directly after the function inside braces.

This is the function

``` swift
func travel(action: () -> Void) {
    print("I'm getting ready to go.")
    action()
    print("I arrived!")
}
```

now, instead of declaring a closure to pass in as parameter,
wenn I call the function I add the {} and inside those I pass the closure which would be the closure parameter

``` swift
travel() {
    print("I'm driving in my car")  // this is the closure which will be as parameter in travel
}
```

this is why is called trailing

and this is ok too!! calling the travel func without the ()
``` swift
travel {
    print("I'm driving in my car")
}
```


#### Using closures as parameters when they accept parameters

This is where closures can start to be read a bit like line noise: a closure you pass into a function can also accept its own parameters.

We’ve been using () -> Void to mean “accepts no parameters and returns nothing”, but you can go ahead and fill the () with the types of any parameters that your closure should accept.

To demonstrate this, we can write a travel() function that accepts a closure as its only parameter, and that closure in turn accepts a string:
``` swift
func travel(action: (String) -> Void) {
    print("I'm getting ready to go.")
    action("London")
    print("I arrived!")
}
```
Now when we call travel() using trailing closure syntax, our closure code is required to accept a string:
``` swift
travel { (place: String) in
    print("I'm going to \(place) in my car")
}
```

#### Using closures as parameters when they return values

We can write a travel() function that accepts a closure as its only parameter, and that closure in turn accepts a string and returns a string:
``` swift
func travel(action: (String) -> String) {
    print("I'm getting ready to go.")
    let description = action("London")
    print(description)
    print("I arrived!")
}
```
Now when we call travel() using trailing closure syntax, our closure code is required to accept a string and return a string:
``` swift
travel { (place: String) -> String in
    return "I'm going to \(place) in my car"
}
```
### Genius - Shorthand parameter names

However, Swift knows the parameter to that closure must be a string, so we can remove it:
``` swift
travel { place -> String in
    return "I'm going to \(place) in my car"
}
```
It also knows the closure must return a string, so we can remove that:
``` swift
travel { place in
    return "I'm going to \(place) in my car"
}
```
As the closure only has one line of code that must be the one that returns the value, so Swift lets us remove the return keyword too:
``` swift
travel { place in
    "I'm going to \(place) in my car"
}
```
Swift has a shorthand syntax that lets you go even shorter. Rather than writing place in we can let Swift provide automatic names for the closure’s parameters. These are named with a dollar sign, then a number counting from 0.
``` swift
travel {
    "I'm going to \($0) in my car"
}
```
and with two parameter to the closure
``` swift
func travel(action: (String, String) -> String ) {
    print("hello")
    let description = action("Berlin","London")
    print(description)
    print("and ciao")
}
travel {
    "driving to \($0) and \($1)"
}
```
or
``` swift

func travel(action: (String, Int) -> String) {
    print("I'm getting ready to go.")
    let description = action("London", 60)
    print(description)
    print("I arrived!")
}
```

We’re going to call that using a trailing closure and shorthand closure parameter names. Because this accepts two parameters, we’ll be getting both $0 and $1:


``` swift
travel {
    "I'm going to \($0) at \($1) miles per hour."
}
```

#### Returning closures from functions

In the same way that you can pass a closure to a function, you can get closures returned from a function too.

The syntax for this is a bit confusing at first, because it uses -> twice: once to specify your function’s return value, and a second time to specify your closure’s return value.

To try this out, we’re going to write a travel() function that accepts no parameters, but returns a closure. The closure that gets returned must be called with a string, and will return nothing.

Here’s how that looks in Swift:
``` swift
func travel() -> (String) -> Void {
    return {
        print("I'm going to \($0)")
    }
}
```
We can now call travel() to get back that closure, then call it as a function:
``` swift
let result = travel()
result("London")
```
It’s technically allowable – although really not recommended! – to call the return value from travel() directly:

``` swift
let result2 = travel()("London")
```

If you use any external values inside your closure, Swift captures them – stores them alongside the closure, so they can be modified even if they don’t exist any more.

Right now we have a travel() function that returns a closure, and the returned closure accepts a string as its only parameter and returns nothing:
``` swift
func travel() -> (String) -> Void {
    return {
        print("I'm going to \($0)")
    }
}
```
We can call travel() to get back the closure, then call that closure freely:
``` swift
let result = travel()
result("London")
```
Closure capturing happens if we create values in travel() that get used inside the closure. For example, we might want to track how often the returned closure is called:
``` swift
func travel() -> (String) -> Void {
    var counter = 1

    return {
        print("\(counter). I'm going to \($0)")
        counter += 1
    }
}
```
Even though that counter variable was created inside travel(), it gets captured by the closure so it will still remain alive for that closure.

So, if we call result("London") multiple times, the counter will go up and up:
``` swift
result("London")
result("London")
result("London")
```

### struct

Variables inside structs are called properties, so this is a struct with one property:
``` swift
struct Sport {
    var name: String
}
 //That defines the type, so now we can create and use an instance of it:

var tennis = Sport(name: "Tennis")
print(tennis.name)
tennis.name = "Lawn tennis"
```
We made both name and tennis variable, so we can change them just like regular variables


These are called stored properties, because Swift has a different kind of property called a computed property – a property that runs code to figure out its value.

We’re going to add another stored property to the Sport struct, then a computed property. Here’s how that looks:
``` swift
struct Sport {
    var name: String
    var isOlympicSport: Bool

    var olympicStatus: String {
        if isOlympicSport {
            return "\(name) is an Olympic sport"
        } else {
            return "\(name) is not an Olympic sport"
        }
    }
}
```
As you can see, olympicStatus looks like a regular String, but it returns different values depending on the other properties.

Property observers let you run code before or after any property changes. To demonstrate this, we’ll write a Progress struct that tracks a task and a completion percentage:
``` swift
struct Progress {
    var task: String
    var amount: Int
}
```
We can now create an instance of that struct and adjust its progress over time:

``` swift
var progress = Progress(task: "Loading data", amount: 0)
progress.amount = 30
progress.amount = 80
progress.amount = 100
```
What we want to happen is for Swift to print a message every time amount changes, and we can use a didSet property observer for that. This will run some code every time amount changes:
``` swift
struct Progress {
    var task: String
    var amount: Int {
        didSet {
            print("\(task) is now \(amount)% complete")
        }
    }
}
```

### Classes
At first, classes seem very similar to structs but they introduce a new, important, and complex feature called inheritance and important differences

The first difference between classes and structs is that classes never come with a memberwise initializer. This means if you have properties in your class, you must always create your own initializer.

``` swift

// must have initializer!

class Dog {
    var name: String
    var breed: String

    init(name: String, breed: String) {
        self.name = name
        self.breed = breed
    }
}

// Class inheritance. it inherits all the properties and methods of the original class, and can add its own on top.

class Poodle: Dog {
// ...
}

// However, we can also give Poodle its own initializer
class Poodle: Dog {
    init(name: String) {
        super.init(name: name, breed: "Poodle")
    }
}

// For safety reasons, Swift always makes you call super.init() from child classes – just in case the parent class does some important work when it’s created.
// Child classes can replace parent methods with their own implementations – a process known as overriding

//lets add the method to dog
    func makeNoise() {
        print("Woof!")
    }
    
// If we create a new Poodle class that inherits from Dog, it will inherit the makeNoise() method. So, this will print “Woof!”:
//Method overriding allows us to change the implementation of makeNoise() for the Poodle class.

//Swift requires us to use override func rather than just func when overriding a method
// in Poodle!
override func makeNoise() {
        print("Yip!")
    }

// sometimes you want to disallow other developers from building their own class based on yours.

Swift gives us a final keyword just for this purpose: when you declare a class as being final, no other class can inherit from it.

final class Dog {
   // ...
}

// The third difference between classes and structs is how they are copied. When you copy a struct, both the original and the copy are different things – changing one won’t change the other. When you copy a class, both the original and the copy point to the same thing, so changing one does change the other.

// The fourth difference between classes and structs is that classes can have deinitializers – code that gets run when an instance of a class is destroyed.

// We’re going to create a few instances of the Person class inside a loop, because each time the loop goes around a new person will be created then destroyed:

for _ in 1...3 {
    let person = Person()
    person.printGreeting()
}

deinit {
    print("\(name) is no more!")
}

//The final difference between classes and structs is the way they deal with constants. If you have a constant struct with a variable property, that property can’t be changed because the struct itself is constant.

//However, if you have a constant class with a variable property, that property can be changed

//If you want to stop that from happening you need to make the property constant:

```

### PROTOCOLS AND EXTENSIONS

Truly Swifty functionality: protocols and protocol-oriented programming (POP).

POP does away with large, complex inheritance hierarchies, and replaces them with much smaller, simpler protocols that can be combined together. This really is the fulfillment of something Tony Hoare said many years ago: “inside every large program, there is a small program trying to get out.”
Protocols are a way of describing what properties and methods something must have. You then tell Swift which types use that protocol – a process known as adopting or conforming to a protocol.

For example, we can write a function that accepts something with an id property, but we don’t care precisely what type of data is used. We’ll start by creating an Identifiable protocol, which will require all conforming types to have an id string that can be read (“get”) or written (“set”):

``` swift
protocol Identifiable {
    var id: String { get set }
}

// We can’t create instances of that protocol - it’s a description, not a type by itself. But we can create a struct that conforms to it:

struct User: Identifiable {
    var id: String
}
// Finally, we’ll write a displayID() function that accepts any Identifiable object:

func displayID(thing: Identifiable) {
    print("My ID is \(thing.id)")
}

```

#### Protocol inheritance

One protocol can inherit from another in a process known as protocol inheritance. Unlike with classes, you can inherit from multiple protocols at the same time before you add your own customizations on top

``` swift
protocol Payable {
    func calculateWages() -> Int
}

protocol NeedsTraining {
    func study()
}

protocol HasVacation {
    func takeVacation(days: Int)
}

//We can now create a single Employee protocol that brings them together in one protocol. 

protocol Employee: Payable, NeedsTraining, HasVacation { }

// ex
func helloNewEmployee(employee : Employee ) {
    print("hello there")
}
struct myEmployee: Employee {
    func calculateWages() -> Int {return 10}
    func study(){}
    func takeVacation(days: Int){ }
    
}


var carl = myEmployee()

carl.calculateWages()
helloNewEmployee(employee: carl)

```
### Extensions
Extensions allow you to add methods to existing types, to make them do things they weren’t originally designed to do.
For example, we could add an extension to the Int type so that it has a squared() method that returns the current number multiplied by itself:
``` swift
extension Int {
    func squared() -> Int {
        return self * self
    }
}

let number = 9

number.squared()
```
Swift doesn’t let you add stored properties in extensions, so you must use computed properties instead. For example, we could add a new isEven computed property to integers that returns true if it holds an even number:
``` swift
extension Int {
    var isEven: Bool {
        return self % 2 == 0
    }
}
```

### Protocol extensions

Protocols let you describe what methods something should have, but don’t provide the code inside. Extensions let you provide the code inside your methods, but only affect one data type – you can’t add the method to lots of types at the same time.

rather than extending a specific type like Int you extend a whole protocol so that all conforming types get your changes.

For example, here is an array and a set containing some names:

Swift’s arrays and sets both conform to a protocol called Collection, so we can write an extension to that protocol to add a summarize() method to print the collection neatly

``` swift
let pythons = ["Eric", "Graham", "John", "Michael", "Terry", "Terry"]
let beatles = Set(["John", "Paul", "George", "Ringo"])

extension Collection {
    func summarize() {
        print("There are \(count) of us:")

        for name in self {
            print(name)
        }
    }
}

// Both Array and Set will now have that method, so we can try it out:

pythons.summarize()
beatles.summarize()

```
### Protocol-oriented programming

Protocol extensions can provide default implementations for our own protocol methods. This makes it easy for types to conform to a protocol, and allows a technique called “protocol-oriented programming” – crafting your code around protocols and protocol extensions.

First, here’s a protocol called Identifiable that requires any conforming type to have an id property and an identify() method:

``` swift
protocol Identifiable {
    var id: String { get set }
    func identify()
}
```
We could make every conforming type write their own identify() method, but protocol extensions allow us to provide a default:

``` swift
extension Identifiable {
    func identify() {
        print("My ID is \(id).")
    }
}
```

Now when we create a type that conforms to Identifiable it gets identify() automatically:

``` swift
struct User: Identifiable {
    var id: String
}

let twostraws = User(id: "twostraws")
twostraws.identify()
```

### OPTIONALS

Null references – literally when a variable has no value – were invented by Tony Hoare way back in 1965
Sir Charles Antony Richard Hoare, is a British computer scientist. He developed the sorting algorithm quicksort in 1959/1960. He also developed Hoare logic for verifying program correctness, and the formal language communicating sequential processes to specify the interactions of concurrent processes and the inspiration for the occam programming language.

Swift’s solution to null references, known as optionals.

if you wanted to store an age property for users, what would you do if you didn’t know someone’s age?

ou might say “well, I’ll store 0”, but then you would get confused between new-born babies and people whose age you don’t know. You could use a special number such as 1000 or -1 to represent “unknown”, both of which are impossible ages, but then would you really remember that number in all the places it’s used?

Swift’s solution is called optionals,

To make a type optional, add a question mark after it.
Optionals are variables that can either have a value or no value at all. Swift is different from many programming languages because normal constants and variables must have a value. This makes Swift a safe language because it prevents your code from failing when a variable is expected to have a value but one hasn’t yet been set.
However, there will be times when you need to create a variable but don’t have a value for it yet. In these cases, you can use an optional.
We didn’t assign an initial value to futureTeacher, so its default value is the special value nil, which means it doesn’t yet have a value.
You can’t set a regular variable to nil. This is a special characteristic of optionals.

``` swift
var age: Int? = nil
// if we later learn that age, we can use it:
age = 38
```

#### Declaration
``` swift
enum Optional<Wrapped>
```
Overview
You use the Optional type whenever you use optional values, even if you never type the word Optional. Swift’s type system usually shows the wrapped type’s name with a trailing question mark (?) instead of showing the full type name. For example, if a variable has the type Int?, that’s just another way of writing Optional<Int>. The shortened form is preferred for ease of reading and writing code.
The types of shortForm and longForm in the following code sample are the same:
``` swift
let shortForm: Int? = Int("42")
let longForm: Optional<Int> = Int("42")
```
The Optional type is an enumeration with two cases. Optional.none is equivalent to the nil literal. Optional.some(Wrapped) stores a wrapped value. For example:
``` swift
let number: Int? = Optional.some(42)
let noNumber: Int? = Optional.none
print(noNumber == nil)
// Prints "true"
```
Another ex
``` swift
let i: Int? = 10
let j = i.map { $0 * 2 }
print(j)
```
the value 10 was taken out of its optional container, multiplied by 2, then placed back into an optional.

If we wanted to print out a welcome message – but only if we got back a username – then optional map is perfect:

``` swift
var username: String? = fetchUsername(1989)
let formattedUsername = username.map { "Welcome, \($0)!" } ??
"Unknown user"
print(formattedUsername)
```

#### Optionals are Enums
Because Optionals are just Enums we can also work with them like Enums.

##### Assigning
``` swift
// z is an optional
var z: Int? = .Some(20)
print(z ?? "sjdhf") // returns 20
var z: Int? = .none
print(z ?? "sjdhf") // returns sjdhf
```  
##### Using switch with Optionals
``` swift
let x: String? = "Hello Optional"
switch x {
case .some(let value): print("Value: \(value)")
case .none: print("nothing stored inside the enum")
}
```
##### Accessing an Optionals value using case let
``` swift
if case let .some(value) = x {
print(value)
}
```
#### UNWRAPPING OPTIONALS
Optionals make your code safer because they force you to plan for a situation in which they have no value. But this also means they require a little more work to use
What happens if we use name.count? A real string has a count property that stores how many letters it has, but this is nil – it’s empty memory, not a string, so it doesn’t have a count.

Because of this, trying to read name.count is unsafe and Swift won’t allow it. Instead, we must look inside the optional and see what’s there – a process known as unwrapping.
#### Optional Binding
with 'if let' ..

``` swift
if let unwrapped = name {
    print("\(unwrapped.count) letters")
} else {
    print("Missing name.")
}
```
#### guard let
An alternative to if let is guard let, which also unwraps optionals. guard let will unwrap an optional for you, but if it finds nil inside it expects you to exit the function, loop, or condition you used it in
However, the major difference between if let and guard let is that your unwrapped optional remains usable after the guard code.
``` swift
func greet(_ name: String?) {
    guard let unwrapped = name else {
        print("You didn't provide a name!")
        return
    }

    print("Hello, \(unwrapped)!")
}
```


#### Forced Unwrapping
One way to unwrap an optional is through forced unwrapping. Use forced unwrapping when you know that an optional has a value and you want the computer to access that value directly. You do this by entering an ! after the optional name. If you force-unwrap an optional and it has a nil value, your program will crash.

For example, if you have a string that contains a number, you can convert it to an Int like this:

``` swift
let str = "5"
let num = Int(str)
```
That makes num an optional Int because you might have tried to convert a string like “Fish” rather than “5”.

Even though Swift isn’t sure the conversion will work, you can see the code is safe so you can force unwrap the result by writing ! after Int(str), like this:

``` swift
let num = Int(str)!
```
 But if you’re wrong – if str was something that couldn’t be converted to an integer – your code will crash.


#### Implicitly Unwrapped 
rather than unwrap the optional every time you use it, you can declare it as an implicitly unwrapped optional. This tells the computer that the variable is an optional but will always have a value. An implicitly unwrapped optional, therefore, does not need to be unwrapped every time you use it; it’s automatically unwrapped for you. Instead of creating the optional with a ? after the data type like a regular optional, you create an implicitly unwrapped optional by typing an ! after the data type.

You might be wondering when you would ever use these implicitly unwrapped optionals. A common use is when you write an app with a storyboard. When you want to connect variables in your code to objects in the storyboard, you make them implicitly unwrapped optionals. You’ll see these come up in Chapter 10 while you’re creating the Birthday Tracker app. These variables need to be optional (because the storyboard requires it), but they will always have a value (since they are connected to the storyboard, the storyboard will always give them a value before you use them).
Other than in this special case, you shouldn’t be using implicitly unwrapped optionals very often. They aren’t as safe

``` swift

let age: Int! = nil

```
Because they behave as if they were already unwrapped, you don’t need if let or guard let to use implicitly unwrapped optionals. However, if you try to use them and they have no value – if they are nil – your code crashes.
#### Nil coalescing
When the optional has a value, the value will be used as usual, but when the optional is nil, the nil coalescing operator will use the default value instead.
ex
``` swift
func username(for id: Int) -> String? {
    if id == 1 {
        return "Taylor Swift"
    } else {
        return nil
    }
}
```

If we call that with ID 15 we’ll get back nil because the user isn’t recognized, but with nil coalescing we can provide a default value of “Anonymous” like this:

``` swift
let user = username(for: 15) ?? "Anonymous"

```

### Optional chaining

Swift provides us with a shortcut when using optionals: if you want to access something like a.b.c and b is optional, you can write a question mark after it to enable optional chaining: a.b?.c.

When that code is run, Swift will check whether b has a value, and if it’s nil the rest of the line will be ignored – Swift will return nil immediately. But if it has a value, it will be unwrapped and execution will continue.

``` swift
let names = ["John", "Paul", "George", "Ringo"]
let beatle = names.first?.uppercased()
```

That question mark is optional chaining – if first returns nil then Swift won’t try to uppercase it, and will set beatle to nil immediately.

### Optional try
Back when we were talking about throwing functions, we looked at this code:
``` swift
enum PasswordError: Error {
    case obvious
}

func checkPassword(_ password: String) throws -> Bool {
    if password == "password" {
        throw PasswordError.obvious
    }

    return true
}

do {
    try checkPassword("password")
    print("That password is good!")
} catch {
    print("You can't use that password.")
}
```
That runs a throwing function, using do, try, and catch to handle errors gracefully.

There are two alternatives to try, both of which will make more sense now that you understand optionals and force unwrapping.

The first is try?, and changes throwing functions into functions that return an optional. If the function throws an error you’ll be sent nil as the result, otherwise you’ll get the return value wrapped as an optional.

Using try? we can run checkPassword() like this:
``` swift
if let result = try? checkPassword("password") {
    print("Result was \(result)")
} else {
    print("D'oh.")
}
```
The other alternative is try!, which you can use when you know for sure that the function will not fail. If the function does throw an error, your code will crash.

Using try! we can rewrite the code to this:
``` swift
try! checkPassword("sekrit")
print("OK!")
```
### Failable initializers

When talking about force unwrapping, I used this code:
``` swift
let str = "5"
let num = Int(str)
```
That converts a string to an integer, but because you might try to pass any string there what you actually get back is an optional integer.

This is a failable initializer: an initializer that might work or might not. You can write these in your own structs and classes by using init?() rather than init(), and return nil if something goes wrong. The return value will then be an optional of your type, for you to unwrap however you want.

### Typecasting

``` swift
class Animal { }
class Fish: Animal { }

class Dog: Animal {
    func makeNoise() {
        print("Woof!")
    }
}

let pets = [Fish(), Dog(), Fish(), Dog()]
```

Swift can see both Fish and Dog inherit from the Animal class, so it uses type inference to make pets an array of Animal.
If we want to loop over the pets array and ask all the dogs to bark, we need to perform a typecast: Swift will check to see whether each pet is a Dog object, and if it is we can then call makeNoise().

This uses a new keyword called as?, which returns an optional: it will be nil if the typecast failed, or a converted type otherwise.

``` swift
for pet in pets {
    if let dog = pet as? Dog {
        dog.makeNoise()
    }
}
```

    

### playing around



``` swift
var int = Int.random(in: 1..<100)
var anInt = 0xa
Int.Magnitude(int)
abs(anInt)

var sign = anInt.signum()
print(sign)
anInt.nonzeroBitCount
Int.max
var pie = 3.1415312

pie.significand
pie.exponent
var last = Double.pi.ulp
```


### Sources:

[Playground tips](https://fluffy.es/xcode-playground-tips/)  
[apple documentation](https://developer.apple.com/documentation/swift/optional)  
[Swift Playground and Markdown](http://www.thomashanning.com/xcode-markup-for-playgrounds/)  

> “The secret to getting ahead is getting started.” Mark Twain


- [Day 1](https://www.hackingwithswift.com/100/1) – variables, simple data types, and string interpolation
- [Day 2](https://www.hackingwithswift.com/100/2) – arrays, dictionaries, sets, and enums
- [Day 3](https://www.hackingwithswift.com/100/3) – operators and conditions
- [Day 4](https://www.hackingwithswift.com/100/4) – loops, loops, and more loops
- [Day 5](https://www.hackingwithswift.com/100/5) – functions, parameters, and errors
- [Day 6](https://www.hackingwithswift.com/100/6) – closures part one
- [Day 7](https://www.hackingwithswift.com/100/7) – closures part two
- [Day 8](https://www.hackingwithswift.com/100/8) – structs, properties, and methods
- [Day 9](https://www.hackingwithswift.com/100/9)– access control, static properties, and laziness
- [Day 10](https://www.hackingwithswift.com/100/10) – classes and inheritance
- [Day 11](https://www.hackingwithswift.com/100/11) – protocols, extensions, and protocol extensions
- [Day 12](https://www.hackingwithswift.com/100/12) – optionals, unwrapping, and typecasting

<hr>

[^1]: What?
