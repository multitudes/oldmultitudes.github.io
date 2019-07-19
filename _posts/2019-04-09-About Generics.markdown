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


One of those exciting new frameworks making heavy use of generics and all those features that they contain is swiftUI.

The syntax here is incredibly lightweight.

To build this list here we start by creating a list struct and then passing in that array of contacts directly to the list.  
This gives us a closure where we get access to each contact and then we're going to create the view that's going to represent each one.  
We're going to use the Vstack type which is a vertical stack and we gonna align all of our elements to the leading edge, which for left-to-right languages would mean on the left.  
Then we're going to create two pieces of text, one for the name of each contact and one for the email address of that contact.

``` swift

struct contactList: View {
    var contacts: [Contact]
    var body: some View {
        List(contacts) { contact in 
            VStack(alignment: .leading) {
                Text(contact.name)
                Text(contact.email)
                }
        }
    }
}


```

So we say `some View`. What is the type here? 
The `some`  keyword is a new feature in Swift 5.1 which is called opaque return type.   
It enables to return any type that conforms to the view protocol as part of this computed property.

The type would be then 
![image](/assets/img/generics/2.png)

it's just how awesome SwiftUI is, because if we are not necessarily seeing all of these types when we're using it.   
All we see is this simple nice declarative API, but then under the hood all these complex generics are created for us.  
This is really powerful and enables Swift UI itself to retain type safety throughout the system.   
It doesn't leak those implementation details out to us for us we just get a simple elegant top-level API but at the same time under the hood generics is really what's powering everything.

Generics should make our top-level code easier and simpler it shouldn't make it harder

### sources

[hacking with Swift live 2019 ](https://youtu.be/y4qFRLp_JNM)  

