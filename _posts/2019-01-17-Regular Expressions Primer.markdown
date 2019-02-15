---
layout: post
title:  "Regular Expressions Primer"
date:   2019-01-17 10:41:47 +0100
categories: Regex, programming, regular expressions
comments: true
published: false
---
<div class="message">
Regular Expressions are one of the most powerful way of using programming languages </div>

They can be used to 'scrub' website to extract links, informations, titles..

They are just simply a series of codes that you use to define exactly what text you are looking for. And text can be numbers letters punctuation etc.

This code is used to match patterns. ets see an example. I want to find all numbers of one to five digit long followed by a space and the words "Hello World". 
Example of the string:

12345 Hello World.

The syntax is for the numbers, I read loud, the slash is delimiting the start of a regular expression.
So this means: A digit between 1 to 5 digits in length, whenever you use these curly brackets, you are saying that you expect between n to m digits 

\d{1,5}

Then this is followed by a space. The Regular expression for a space is 

\s

Then you expect a series of character which will be a serie from 1 to multiple letters in length. This 'w' represents anything which is a character, and the '+' means one or more.

\w+

again followed by space and a word

\s\w+

then the point. The point can be interpreted in regex to mean any character except a newline. So I nee to put a backslash.

\.

We now put all this together:

\d{1,5}\s\w+\s\w+\.

So lets see a bit of theory now.

\d   is any number (digit)
\D   with the capital D is anything but a number (digit)
\s   A space
\S   Anything but a space
\w   Any character
\W   Anything but a character
.    matches any character except a line break
\b   match for a space which precedes or follows a whole word

?    zero or one repetition of the code which precedes it
*    One or more repetition
{n}  If you know exactly how many repetitions, insert the amount in curly brackets
{m,n} Here means m to n repetitions as seen above

\e    escaped whitespace
\f    form feed
\n    newline
\r    carriage return
\t    horizontal tab
 
Using [] brackets to find commonly mispelled words. 

Example tomorrow can be mispelled as tommorow, tommorrow..

We can find these like this



That's it for now. If I missed something let me know in the comments! 



