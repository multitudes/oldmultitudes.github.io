---
layout: post
title:  "How float point arithmetics can screw up your code"
date:   2019-01-16 10:41:47 +0100
categories: programming
comments: true
published: false
---
<div class="message">
 </div>

### 

Accuracy
Floating Point Arithmetic
To understand accuracy, we first need to look at how computers (which are finite and discrete) store numbers (which are infinite and continuous)
Exercise
Take a moment to look at the function $f$ below.  Before you try running it, write on paper what the output would be of $x_1 = f(\frac{1}{10})$.  Now, (still on paper) plug that back into $f$ and calculate $x_2 = f(x_1)$.  Keep going for 10 iterations.

This example is taken from page 107 of *Numerical Methods*, by Greenbaum and Chartier.

{% highlight python %}

def f(x):
    if x <= 1/2:
        return 2 * x
    if x > 1/2:
        return 2*x - 1

{% endhighlight %}



x = 1/10
for i in range(80):
    print(x)
    x = f(x)
What went wrong?
#### Problem: math is continuous & infinite, but computers are discrete & finite

Two Limitations of computer representations of numbers:
1. they can't be arbitrarily large or small
2. there must be gaps between them

The reason we need to care about accuracy, is because computers can't store infinitely accurate numbers.  It's possible to create calculations that give very wrong answers (particularly when repeating an operation many times, since each operation could multiply the error).



   

### Resources 

That's it for now. If I missed something let me know in the comments! 



