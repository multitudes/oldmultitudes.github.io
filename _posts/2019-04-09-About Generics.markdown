---
layout: post
title:  "About Generics in Swift"
date:   2019-06-15
categories: iOS, developer
comments: true
published: true
---
> Generics is really key to fundamentally understanding how a lot of how Swift works.

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

Generics should make our top-level code easier and simpler it shouldn't make it harder.

## Generics are implemented in Protocols

One way we can see the ower of Generics is by looking at how protocols are implemented.
Example:
Imagine a Drawable protocol defined with Generics, it can then be specialized to Text, Strings, shapes and all sorts of object.

``` swift
extension Shape: Drawable {
    func draw( in  context: VectorDrawingContext){
        points.forEach(context.add)
    }
}
extension Text: Drawable {
    func draw( in  context: TextDrawingContext){
            context.font = font
            context.add(String)
        }
}
```

What we've essentially done here is that we've taken a bunch of different use cases like drawing images, texts, shapes etc and we've built a common shared API on top of that.
Having a shared API is not only great for code elegance kind of sake it's also great for getting into a new codebase. If someone new joined our team now we can just point them to this function and that's all they need to know in order to use our drawing code.

Equally important is that we can actually build really powerful abstractions on top of our API.

We can extend an array which isn't a generic,  so we can say, that array will now conform to drawable when the elements in that array also conform to drawable, and then we can implement draw for an array but not for any array, just for the ones that contains drawable elements.   

So we can retain the type safety just how swift UI use generics to retain the type safety we can do the same thing here.

``` swift
extension Array: Drawable where Element: Drawable {
    func draw(in context: Element.context) {
        forEach { $0.draw(in: context)
        }
    }
}
```

Even though this code here might look a little bit more complex, it's an implementation detail, and the API user or someone using our code, don't need to know about these details.


We can introduce all these new types and we can still use that same image from the same function with any of them.  
What we can see here through this example is that generics are really great we want to reuse some of our core logic for different use cases and they can let us build powerful shared abstractions



POP is what many people refer to as protocol oriented programming. Protocol oriented programming and generics are very highly related.  

![image](/assets/img/generics/3.png)

Not everything should be programmed with generics in mind.
Things can go wrong where generics might not be the right tool for the problem, for ex. a protocol contactable, for a contact list.
This because generics are great when we want to generalize a problem and then create multiple specializations of it. So in this case we have our contactable generalization but it's just about being a contact in the implementation. We have only one specialized case and we do not need a generic

### to recap

- generics they're truly great we want to model a concept a given concept that's a generic one for multiple use.

- the goal of deploying generics should be to make our top-level code simpler not harder or more complicated.

- when used in the right situations generics can be incredibly powerful and they can let us reuse both code and concepts throughout shared abstractions.


### sources

[hacking with Swift live 2019 ](https://youtu.be/y4qFRLp_JNM)  

