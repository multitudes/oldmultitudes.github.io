---
layout: post
title:  "Elements of Functional programming in Swift"
date:   2010-05-23
categories: iOS, developer
comments: true
published: true
---

<!--

<div class="message">
"Any fool can write code that a computer can understand, but good programmers write code that humans can understand"
<br><cite>Martin Fowler</cite>
</div>
-->
<div class="message">
"Classes are about as welcome in functional code as a hedgehog in a hemophilia convention."
<br><cite>Paul Hudson</cite>
</div>
<!--
<div class="message">
"express what we want to achieve, rather than how this is implemented.
<br><cite>Javier Soto</cite>
</div>
<div class="message">
"the only way to learn a new programming language is by writing programs in it."
<br><cite>Dennis Ritchie</cite>
</div>
-->


This is a blog post inspired by the excellent Swift course by Paul Hudson [Hacking with Swift](). 


What is functional programming?  

Functional programming (often abbreviated FP) is the process of building software by composing pure functions, avoiding shared state, mutable data, and side-effects.


In Object Oriented Programming, a class blends state, functionality, inheritance, and more. We will see that functional programming can dramatically simplify your code. 

### Five principles of functional programming

- Functions are first-class data types. That means they can be created, copied, and passed around like integers and strings. 
- Functions can be used as parameters to other functions. 
- In order to allow our functions to be re-used in various ways, they should always return the same output when given specific input, and not cause any side effects. 
- Because functions always return the same output for some given input, we should prefer to use immutable data types rather than using functions to change mutable variables. 
- Because our functions don't cause side effects and variables are all immutable, we can reduce how much state we track in our program – and often eliminate it altogether.

You should already know that functions are first-class data types in Swift – after all, you can copy closures and pass them around. So, that's one down. Next up, passing functions as parameters to other functions is also something you maybe have done already, such as calling sort() with a closure.  

You might come across the name "higher-order function", which is the name given to a function that accepts another function as a parameter.  

Where things get more a bit more complicated – but a lot more interesting – is when we write functions that always produce the same output for a given input. This means if you write a function lengthOfStrings() that accepts an array of strings and returns back an array of integers based on the length of each string, that function will return [6, 4, 5] when given ["Taylor", "Paul", "Adele"]. It doesn't matter what else has happened in your program, or how often the function has been called: the same input must return the same output.  

A function that always returns the same result for a given input without causing side effects is often called a pure function. 

If a function does something like writing to disk, is that a side effect or in fact just the main point of the function?   
Functional programmers should aspire to create pure functions.



The lack of state can be tricky, because it's so deeply baked into object orientation. "State" is a series of values stored by your program, it includes caching things to increase performance, and also important things like user settings. The problem comes when this state gets used inside a function, because it means the function is no longer predictable.  
Using the lengthOfStrings() example from earlier, consider what would happen if we had a boolean setting called returnLengthsAsBinary – the function that would always return [6, 4, 5] when given ["Taylor", "Paul, "Adele"] could now also return ['110', '10', '101'] depending on the value of something completely external. 

When all five of these principles combine, you get a number of immediate, valuable benefits. 

When you write functions that produce predictable output, you can write unit tests for them trivially. 


### The map() method

map() works great on collections and optionals

``` swift
let names = ["Taylor", "Paul", "Adele"]

func lengthOfStrings(strings: [String]) -> [Int] {
    var result = [Int]()
    for string in strings {
        result.append(string.characters.count)
}
    return result
}
```

That function takes an array of strings and returns an array of integers based on those strings. 

we can replace all that code with this:

``` swift
func lengthOfStrings(strings: [String]) -> [Int] {
    return strings.map { $0.characters.count }
}
```

the functional version conveys significantly more meaning to the compiler

the type signature hasn't changed.you can upgrade your code bit by bit rather than all at once.
Another ex
``` swift

let fruits = ["Apple", "Cherry", "Orange", "Pineapple"]
let upperFruits = fruits.map { $0.uppercased() }
print(upperFruits)
>>> ["APPLE", "CHERRY", "ORANGE", "PINEAPPLE"]

// 
let scores = [100, 80, 85]
let formatted = scores.map { "Your score was \($0)" }
print(formatted)
>>> ["Your score was 100", "Your score was 80", "Your score was 85"]
// 
let scores = [100, 80, 85]
let passOrFail = scores.map { $0 > 85 ? "Pass" : "Fail" }
let position = [50, 60, 40]
let averageResults = position.map { 45...55 ~= $0  ? "Within
average" : "Outside average" }

// with ternary operator
let scores = [100, 80, 85]
let passOrFail = scores.map { $0 > 85 ? "Pass" : "Fail" }
let position = [50, 60, 40]
let averageResults = position.map { 45...55 ~= $0  ? "Within
average" : "Outside average" }


```
map() has that name because it specifies the mapping from one array to another. 

### Optional map
a value inside a container is exactly what optionals are. They are defined like this:

``` swift
enum Optional<Wrapped> {
case None
case Some(Wrapped)
}

let shortForm: Int? = Int("42")
let longForm: Optional<Int> = Int("42")

let number: Int? = Optional.some(42)
let noNumber: Int? = Optional.none
print(noNumber == nil)
// Prints "true"
```

We can use map() on optionals too. The principle is identical: take value out of container, apply function, then place value back in the container again.

### forEach

also loops over an array and executes a function on each item. The difference lies in the return value: map() returns a new array of items, whereas forEach() returns nothing at all – it's just a functional way to loop over each item.
by using forEach() you're making it clear you're not manipulating the contents of the array, which allows the Swift optimizer to do a better job.  

``` swift
["Taylor", "Paul", "Adele"].forEach { print($0) }
```

### compactMap()


Using flatMap on a sequence (like an Array) filtering anything that maps to nil is now deprecated and replaced by compactMap.

The compactMap () function maps items in array A into array B using a function you provide, then flattens the results using concatenation which converts that array of arrays into a single array.

``` swift
let albums: [String?] = ["Fearless", nil, "Speak Now", nil, "Red"]
let result = albums.map { $0 }
print(result)
//[Optional("Fearless"), nil, Optional("Speak Now"), nil, Optional("Red")]

```
That's a lot of optionals, with some nils scattered through. Switching to compactMap() rather than map() can help:

``` swift
let result = albums.compactMap { $0 }
print(result)
// ["Fearless", "Speak Now", "Red"]
```

The optionals are gone and the nils are removed – perfect!  
Whereas map() will retain the optionality of the items it processes, compactMap() will strip it out. So, in the code below, mapResult is of type [String?] and compactMapResult is of type [String].

### Optional compact map

We can use it to flatten the resulting array to remove the optionality and any invalid values. If you have an array of input items, and a transformation function that will return either a transformed item or nil if the transformation failed, this technique is ideal.

``` swift
let scores = ["100", "90", "Fish", "85"]
let compactMapScores = scores.compactMap { Int($0) }
print(compactMapScores)
```

Any throwing function can be used with try?, which translates it to a function that returns nil on failure.  
``` swift
let files = (1...10).flatMap { try? String(contentsOfFile: "someFile-
\($0).txt") }
print(files)
// returns []
```

That will load into an array the contents of someFile-1.txt, someFile-2.txt, and so on. Any file that don't exist will throw an exception, which try? converts into nil, and flatMap() will ignore – all with just one line of code!

### filter()

The filter() method loops over every item in a collection, and passes it into a function that you write. If your function returns true for that item it will be included in a new array, which is the return value for filter().

For example, the code below creates an array of the first 10 numbers in the Fibonacci sequence, then filters that array to include only items that are even:
``` swift
let fibonacciNumbers = [1, 1, 2, 3, 5, 8, 13, 21, 34, 55]
let evenFibonacci = fibonacciNumbers.filter { $0 % 2 == 0 }
// [2, 8, 34]
```

So, the code will run, and pass the number 1 into the closure, making 1 % 2 == 0, which is false. As a result, 1 will not be included in the result array. When it reaches true, that will be included because 2 % 2 == 0 is true.
As with map(), the order items are filtered is out of our control – Swift is free to apply any optimizations it wants to make filtering go faster.



``` swift
let names = ["Michael Jackson", "Taylor Swift", "Michael Caine",
"Adele Adkins", "Michael Jordan"]
let result = names.filter { $0.hasPrefix("Michael") }
//
```


``` swift
let words = ["1989", "Fearless", "Red"]
let input = "My favorite album is Fearless"
let result2 = words.filter { input.contains($0) }
```
 If you want to strip nil but retain optionality, use filter() like this:

``` swift
let words: [String?] = ["1989", nil, "Fearless", nil, "Red"]
let result = words.filter { $0 != nil }
//[Optional("1989"), Optional("Fearless"), Optional("Red")]

```
When presented with a dictionary: you get back a dictionary containing the result,
``` swift
let scores = ["Paul": 100, "Taylor": 95, "Adele": 90, "Michael": 85,
              "Justin": 60]
let goodScores = scores.filter { $1 > 85 }
print(goodScores)

//["Adele": 90, "Paul": 100, "Taylor": 95]
```
### reduce()

The reduce() function condenses an array into a single value by applying a function to every item.
``` swift
func reduce(initial: T, combine: (T, Int) throws -> T)
// or

func reduce(initial: String, combine: (String, Int) throws -> String)


```
Here T stay for type, could be any letter.

Each time the function is called, you get passed the previous value from your function as well as the next item in your array. I've already used it a couple of times elsewhere in this book, using this example:
``` swift
let scores = [100, 90, 95]
let result = scores.reduce(0, +)
// 285
// or

let codes = ["abc","def","ghi"]
let text = codes.reduce("", +)
// "abcdefghi"
```
That will make result equal to 285 by adding 0, 100, 90, and 95. The 0 is the initial value, which is used the first time your function – in this case + is called

The combine argument is a closure so you can also write reduce using the trailing closure syntax:
``` swift
let names = ["alan","brian","charlie"]
let csv = names.reduce("===") {text, name in "\(text),\(name)"}
// "===,alan,brian,charlie"
```


Another ex
``` swift
let result = scores.reduce("") { $0 + String($1) }
print(result)
```

now try
``` swift
let names = ["Taylor", "Paul", "Adele"]
// your code here
print(count)
```
my code
``` swift
let names = ["Taylor", "Paul", "Adele"]
let namesCharCount = names.map{ $0.count }
let sumNames = namesCharCount.reduce(0, +)
```
or 

``` swift
let names = ["Taylor", "Paul", "Adele"]
let count = names.reduce(0) { $0 + $1.count }
print(count)

```

### Reducing to a boolean

A common programming task is to check whether all items in array evaluate to true for a given condition.  

``` swift
let names = ["Taylor", "Paul", "Adele"]
let longEnough = names.reduce(true) { $0 && $1.count > 4 }
print(longEnough)
```


``` swift



``` swift



``` swift



``` swift



``` swift



``` swift



``` swift



===================

one of them is immutability. 
avoids states
good functional code is composable 
you write small functions
that do one maybe two things then
combine together to make bigger
functions like Lego bricks. 
good functional code allows
us to express our intent clearly. it
clarifies our intent.


Dumas said English is just French badly pronounced 

### Useful terms

monads
functors
applicative 
"lightweight encounters" - You dip in, get some quick wins and run away before it gets too hard.



### Sources:
[Paul Hudson - Elements of Functional Programming](https://www.dotconferences.com/2018/01/paul-hudson-elements-of-functional-programming)
[Teaching Swift at Scale - Paul Hudson](https://vimeo.com/291590798)
[SwiftConf '18 - Paul Hudson: Mastering iOS Animation](https://www.youtube.com/watch?time_continue=41&v=_4McEnarqNc)
[https://learntalks.com/tag/paul-hudson/](https://learntalks.com/tag/paul-hudson/)
[Use Your Loaf](https://useyourloaf.com)



<hr>

[^1]: What?




Swift is not a functional language or a true functional language.


L'anglais n'est que du français mal prononcé." "English is just badly pronounced French." D'Artagnan Alexandre Dumas
