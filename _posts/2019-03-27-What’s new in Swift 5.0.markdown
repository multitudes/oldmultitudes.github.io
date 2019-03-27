---
layout: post
title:  "What’s new in Swift 5.0"
date:   2019-03-27 10:41:47 +0100
categories: Swift, iOS
comments: true
published: true
---
<div class="message">
<br>
<cite> </cite>
</div>

![image](/assets/img/whatsnewinswift5.jpg)

The new version of the Swift operating system has just been released this monday (25th March 19) and include quite a few new features and some of them quite advanced.

I just started this month learning Swift so I am quite new. I was following the excellent course []() by Paul Hudson together with the 100 days Swift Challenge and I was happy to hear that he already made the code Swift 5 proof! Amazing. Love this guy! 
And if you are new to Swift like me check out this beta app as well. Quite cool and Swift 5 compatible, has to be installed through testflight. 
https://t.co/6kCV0AdrWG

![image](/assets/img/hundreddaysofswift5.png)

However the [playground](https://github.com/twostraws/whats-new-in-swift-5-0) he released with the new features cannot be run on my MacBookPro anymore. I was using a maxed out 2010 MBP with High Sierra installed, fast SSD and full capacity RAM and I was hope to keep working on it for another year or so. Unfortunately the new version of Swift has to be run under macOS Mojave. Probably it is time to update! If you have any suggestion about the best machine to develop for iOS then pls let me know in the comments.
I have been reading this review by Marco Armenti about the new [Mac Mini](https://marco.org/2018/11/06/mac-mini-2018-review) and really I am temped to go for the middle option, with i5 processor and 256 GB SSD. Sounds like a good value for money. Especially it is portable and quite as powerful as the new MBP.   

Luckily I am using an iMac at school with mojave so I could experiment a bit. Some of the new features are quite advanced for my level but I really like so far the raw strings and the new integer method. 

## This is a summary of the new features

### ABI stability
> ABI is the Application Binary Interface, the specification to which independently compiled binary entities must conform to be linked together and executed. 

It is how the compiler builds an application and how parameters are passed to functions and where the return value is placed for return, plus how exceptions propagate.
ABI stability means locking down the ABI for future compiler versions.

An advantages of ABI stability is that the language would keep evolving but the changes to the ABI from that point on would be additive and the code written from this point on would be compatible with the newer versions of the language.


### A new Result type

Useful in handling errors in complex code such as asynchronous APIs.

### Raw strings

Backslashes and quote marks are interpreted as literal symbols rather than escapes characters or string terminators. Regular expressions in particular will benefit.

The syntax is: place `#` before and after the string, and interpolation will have an extra `#` like this:

{% highlight swift %}
let age = 82
let Eliane = #"My Mother's age is : \#(age)."#
{% endhighlight %}

and regular expressions are more readable:

{% highlight swift %}
let regex = #"\\[A-Z]+[A-Za-z]+\.[a-z]+"#
{% endhighlight %}

### Customizing string interpolation

Swift 5 string interpolation system is now more efficient and more flexible, and it’s creating a whole new range of features that were previously impossible.

### Dynamically callable types

Swift now has a new @dynamicCallable attribute and makes it easier for Swift code to work alongside dynamic languages such as Python and JavaScript.

### Handling future enum cases

Now Swift adds the ability to distinguish between enums that are fixed and enums that might change in the future.

### Flattening nested optionals resulting from try?
Nested optionals are flattened to become regular optionals.

### Checking for integer multiples

This is cool. there is a new method to integers:
`isMultiple(of:)` 
This allows to check whether one number is a multiple of another instead of using the division remainder operation, %.

### Transforming and unwrapping dictionary values with compactMapValues()


### a new count(where:) method

`count(where:)` method will perform the equivalent of a filter() and count in a single pass.



That's it for now. If I missed something let me know in the comments! 
