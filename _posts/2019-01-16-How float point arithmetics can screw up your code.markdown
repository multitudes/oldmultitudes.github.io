---
layout: post
title:  "How float point arithmetics can screw up your code"
date:   2019-01-16 10:41:47 +0100
categories: programming
comments: true
published: true
---
<div class="message">
[e to the pi minus pi](https://imgs.xkcd.com/comics/e_to_the_pi_minus_pi.png)
 </div>

## Accuracy of Floating Point Arithmetic

The fact that floating-point numbers cannot precisely represent all real numbers, and that floating-point operations cannot precisely represent true arithmetic operations, leads to many surprising situations. This is related to the finite precision with which computers generally represent numbers.

Exercise:
This example is taken from page 107 of *Numerical Methods*, by Greenbaum and Chartier.

Take a moment to look at the function $$f$$ below.  Before you try running it, write on paper what the output would be of 

$$x_1 = f(\frac{1}{10})$$ 

Now, (still on paper) plug that back into $$f$$ and calculate $$x_2 = f(x_1)$$.  Keep going for 10 iterations.


{% highlight python %}

def f(x):
    if x <= 1/2:
        return 2 * x
    if x > 1/2:
        return 2*x - 1

{% endhighlight %}

We probably managed to get this results:

`0.1`,`0.2`,`0.4`,`0.8`,`0.2`,`0.4`,`0.8`,`0.2`,`0.4`,`etc`

Now let the computer calculate this for us:

{% highlight python %}
x = 1/10
for i in range(80):
    print(x)
    x = f(x)
    
{% endhighlight %}    

and we get this instead!

`0.1`
`0.2`
`0.4`
`0.8`
`...`
`0.40625`
`0.8125`
`0.625`
`0.25`
`0.5`
`1.0`
`1.0`
`1.0`



What went wrong?

To understand accuracy, we first need to look at how computers (which are finite and discrete) store numbers (which are infinite and continuous)


#### Problem: math is continuous & infinite, but computers are discrete & finite

Two Limitations of computer representations of numbers:
1. they can't be arbitrarily large or small
2. there must be gaps between them

The reason we need to care about accuracy, is because computers can't store infinitely accurate numbers.  It's possible to create calculations that give very wrong answers (particularly when repeating an operation many times, since each operation could multiply the error).

**Machine Epsilon**

Half the distance between 1 and the next larger number. This can vary by computer.  IEEE standards for double precision specify $$ \varepsilon_{machine} = 2^{-53} \approx 1.11 \times 10^{-16}$$

### Expensive Errors

The below examples are from Greenbaum & Chartier.

The European Space Agency spent 10 years and $7 billion on the Ariane 5 Rocket.
This is what can happen when you try to fit a 64 bit number into a 16 bit space (integer overflow):

Here is a floating point error that cost Intel $475 million:
[1994 NYTimes article about Intel Pentium Error](http://www.nytimes.com/1994/11/24/business/company-news-flaw-undermines-accuracy-of-pentium-chips.html)

### Sources 

- [*Numerical Methods*](https://press.princeton.edu/titles/9763.html), by Greenbaum and Chartier
- [Numerical Linear algebra](https://people.maths.ox.ac.uk/trefethen/text.html), by Lloyd N. Trefethen and David Bau, III
- [*Handbook of Floating-Point Arithmetic*](http://www.springer.com/gp/book/9780817647049). The [Chapter 1](https://perso.ens-lyon.fr/jean-michel.muller/chapitre1.pdf) is free. 
- This blog post [What you never wanted to know about floating point but will be forced to find out](http://www.volkerschatz.com/science/float.html)


That's it for now. If I missed something let me know in the comments! 



