---
layout: post
title:  "Scripting in C# for AR and VR applications in Unity"
date:   2010-04-09
categories: iOS, developer
comments: true
published: true
---


<div class="message">
"To code is 1% inspiration, 99% iteration" 
<br><cite>Freely taken from Thomas Edison</cite>
</div>

![image](/assets/img/CSharpScriptingPost.jpg)

### Introduction to C# Programming and Unity

C# is a programming language that's been around since 2001.

It's one of the programming languages included in Microsoft's .NET framework, and is the preferred language to use when we write scripts in the Unity game engine.
When we learn a new language, like English or C#, we need to learn both the syntax and the semantics of that language. 
The syntax is about the structure of statements in a computer language. 
When to open a bracket, where to put the semicolons etc.
Semantics, on the other hand, relates to the meaning of the sentences (or instructions) we build. For example, the English sentence "The large blue fox jumped over the moon" is grammatically correct, but it doesn't really make sense. 
Similarly, we can also create C# statements that are syntactically correct but don't really make sense.
The first step is to type our program in using either an editor (like Microsoft Notepad) or an Integrated Development Environment (IDE) (like Visual Studio Community 2015). 
Because IDEs are so much more powerful than basic editors.
Programming languages fall into two classes for this step: interpreted languages and compiled languages. In interpreted languages, an interpreter converts the program one statement at a time and the CPU executes the instructions as they're converted. This can be very helpful as you're developing your program, but it can also be fairly slow because you're doing the conversion while you run your program. In compiled languages, a compiler converts the entire program to the machine instructions; you can then have the CPU run those instructions.
So is C# a compiled language or an interpreted language? Well, it's actually both! That's one of the characteristics that makes C# such a powerful programming language. When we compile our C# programs, the compiler doesn't actually generate machine instructions; instead, it generates something called Common Intermediate Language (CIL). The CIL, which you can think of as .NET instructions, isn't specific to any particular CPU, which makes the CIL portable to any machine. When it's time to actually run the program, the CIL is interpreted into machine instructions by the .NET Common Language Runtime (CLR). This hybrid approach gives C# great portability.
We start with our C# program or our C# source code, and we run a compiler on it. The compiler is a piece of software that converts that C# source code into what's called Common Intermediate Language. After we have our Common Intermediate Language when it is time to actually run the code somewhere, the dot net Common Language Runtime takes that CIL or Common Intermediate Language and turns it into the actual machine instructions that will run on the chip on that particular computer it's running on.


The first thing we see in the application class is the place where we say we'll be using other namespaces and classes. Namespaces and classes are collections of useful C# code that someone else has already written

One example is a class that will generate random numbers for us. That class (called, surprisingly enough, Random) is found in the System namespace, so when we need it, we'll include the following line in our program:

This tells the compiler that you want access to the classes in the System namespace.

{% highlight csharp %}

using System;

{% endhighlight %}







#### Comments in C# work with xml tags:

{% highlight csharp %}
/// <summary>
/// A class to print a rain message
/// </summary>

// line comment
/* or another comment over more than one line 
*/
{% endhighlight %}



All the application classes we write will have a method called Main. The Main method is the main entry point for the application; when we run our program”

{% highlight csharp %}
static void Main(string[] args)
{% endhighlight %}

We'll talk about the words in front of Main (static and void) as we need them. The part that says (string[] args) lets people use something called "command-line arguments.”

#### Variables

In c# just declaring a variable of a simple type allocates memory.

We declare a variable by putting a data type first, so that the compiler knows how to interpret the ones and zeros, and knows how much memory to allocate for this particular variable. And then we put the variable name, so that we as programmers can refer to that memory location by name rather than by memory address. Optionally, we can also give the the variable a value when we declare that, and we'll see that when we start talking about integers in the following lecture. 
So, what about constants? Well, constants work essentially the same way except that we provide a data type. First, we provide a keyword const, then we provide the data type of the constant, then we provide its name, and then we have to give it a value. We don't optionally give constant values, we have to give them values when we declare them.

##### Integers

Integers or whole numbers, are those numbers that have no fractional or decimal part

In C# there are byte, short, int and long.
Byte uses 8 bits, and short uses 16. Int uses 32, and long uses 64

There is a distinction between value types and reference types. 
The bit get interpreted in a particular way based on the data type we've declared a variable at that memory location to be. For value types, like bytes, short, int and long, the bits at that memory location are in fact interpreted as an integer, a whole number.

For reference types, those bits are interpreted as something different. They're interpreted as a memory address. 
This is the difference between value type and reference types and certainly the numeric types in C#, our value types.

##### Floats

So real numbers are those numbers that have a decimal point. And we actually have a problem as we try to represent real numbers in a computer because real numbers are in what's called the continuous domain. There are an infinite number of real numbers between zero and one, for example, and we know though that two to the b equal n. And so given a limited number of bits, we can only represent a finite number for n, so it's actually impossible for us to represent the whole range of infinite real numbers in a computer. So we actually have to do our representation in something called the discrete domain, not the continuous domain, and this discrete domain is what we use zeros and ones to represent things in. So we can represent lots of real numbers but we can't represent all real numbers. And what that leads to is some inaccuracy in the numbers that we can represent. 

To represent these real numbers we use something called floating numbers and that's just the way we represent real numbers in a computer. And the two data types we'll commonly use are float and double. And in fact, in game development in our unity game development, we're regularly going to just use float just as we regularly use int even though we have a number of different integer data types we can use

##### Math class. 

It is a static class because I call the methods from the class name. Ex Math.cos
It returns a double. We provide a double as parameter. But wait.. it is an angle in radiant !

(float)Math.cos(45)  		// wrong we need radiants.
360 degrees = 2 pi radiants.
Pi/180 = radiants

The constant to use is Math.PI 
45 * Math.PI / 180





NPC (Non-player character. In video games, this usually means a character controlled by the computer via algorithmic, predetermined or responsive behavior, but not necessarily true artificial intelligence.)

CIL: Common Intermediate Language  
Common is included in the name because all the .NET languages (VB, C#, etc.) are compiled to CIL.







### Sources:

arctangent 
Math.Atan2(Double, Double) Method
https://www.mathsisfun.com/algebra/trig-inverse-sin-cos-tan.html

https://docs.microsoft.com/en-us/dotnet/api/system.math?redirectedfrom=MSDN&view=netframework-4.8

[]()

<hr>
