---
layout: post
title:  "Some Swift tips for beginner and intermediate"
date:   2019-05-23
categories: iOS, developer
comments: true
published: false
---


<div class="message">
"With iOS 12, ARKit includes a built-in viewer for displaying and sharing high-quality 3D content using Pixar's usdz file format. " 
<br><cite>Paul Hudson</cite>
</div>

<a rel="ar" href="/assets/img/AR-QL-Pictures/retrotv.usdz">
    <img src="/assets/img/AR-QL-Pictures/Screenshot5.jpg">
</a>

Swift is what’s known as a type-safe language, which means that every variable must be of one specific type

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

### Sources:

[Integrating Apps and Content with AR Quick Look - developer.apple.com](https://developer.apple.com/videos/play/wwdc2018/603/)
<hr>

[^1]: What?