---
layout: post
title:  "About Generics in Swift"
date:   2019-06-15
categories: iOS, developer
comments: true
published: true
---
# draft 

Generics is really key to fundamentally understanding how a lot of how Swift works.

Open the terminal and type:

``` bash
man swift
```

This is the manual entry for the Swift compiler and you will get the following:

![image](/assets/img/generics/1.png)

The first sentence reads:
> swift -- Safe, fast, and expressive general-purpose programming
language

Swift puts a high high focus on type safety and leveraging the compiler in order to produce more safe code that is less prone to runtime errors and lets us write code that is more robust .

This works in Swift is because of generics. 

An array in Swift is implemented as a generic struct: 

``` swift
public struct Array<Element> {
...
}
```
Element here is a generic Type which means that it can be anything!
Any type, class enum struct etc.  

Array is first of all a generalization of a given concept, concept of storing different elements sequentially in memory.
Then this specializes into any number of concrete use cases so for example we can create an array of strings, telling the generics into being bound to the string type.

> Generics all about generalizing a piece of code so it's no longer tied to a single concrete type, and then allowing that code to be specialized for any number of use cases 

## SwiftUI


One of those exciting new frameworks making heavy use of generics and all those features that they contain is swift UI.



### sources

[hacking with Swift live 2019 ](https://youtu.be/y4qFRLp_JNM)  

