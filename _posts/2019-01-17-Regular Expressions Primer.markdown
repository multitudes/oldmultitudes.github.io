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

`\d{1,5}`

Then this is followed by a space. The Regular expression for a space is 

`\s`

Then you expect a series of character which will be a serie from 1 to multiple letters in length. This `w` represents anything which is a character, and the `+` means one or more.

`\w+`

again followed by space and a word

`\s\w+`
then the point. The point can be interpreted in regex to mean any character except a newline. So I nee to put a backslash.

`\.`

We now put all this together:

`\d{1,5}\s\w+\s\w+\.`
So lets see a bit of theory now.

`\d`   is any number (digit)
`\D`   with the capital D is anything but a number (digit)
`\s`   A space
`\S`   Anything but a space
`\w`   Any character
`\W`   Anything but a character
`.`    matches any character except a line break
`\b`   match for a space which precedes or follows a whole word

`?`    zero or one repetition of the code which precedes it
`*`    One or more repetition
`{n}`  If you know exactly how many repetitions, insert the amount in curly brackets
`{m,n}` Here means m to n repetitions as seen above

`\e `   escaped whitespace
`\f `   form feed
`\n`    newline
`\r`    carriage return
`\t `   horizontal tab
 
Using `[]` brackets to find commonly mispelled words. 

Example tomorrow can be mispelled as tommorow, tommorrow..

We can find these like this
`\tom[m]or[r]ow`

[a-z]    any lower case letter
[A-Z]    any upper case letter
[0-9]    any number 
[a-cC-R3-4]  any letter from a to c or uppercase letter from C to R or number from 3-4

Lets look for the name Catherine in our text. But we want to find her last name as well.

We will use the OR operator `|` because we want to find the name but also the shorter verions of her name such of Cath or Cathy, followed by a trailing space and another word of one of more characters:

`\Cat(herine|h)\b\w+\b`

This is the same as 

`\(Catherine|Cath)\b\w+\b`

if I add `\1` at the end, it means take what it is in the parentheses and redo it again 

`\(Catherine|Cath)\b\w+\b\1`  same as `\(Catherine|Cath)\b\w+\b\(Catherine|Cath)`

The caret `^` means at the beginning of the text.
So to find all sentences starting with `Dog`

`(^Dog\s.+$)`   this means all lines starting with dog followed by a space and any or more chars (but no newline) and ending ($).

### with Python

So now we apply what we have learned to use it in python

# import our regex library
import re
# lets take a random text
# if we have a file we can use open('filename.txt')
text = "aAsdfgh$%#n Cat iuhi"
# define our regular expression in the function compile
expression = re.compile('Cat')
# tell python to look for it
pattern = re.search(expression, text)
# print the result using the group function
print(pattern.group())

# To find all occurrences there is the method findall
# lets print all the letters and only the letters in our text:

for line in text:
    strToSearch += text
    
print(strToSearch)    

expression = re.compile('[a-z]',re.IGNORECASE)
pattern2 = re.findall(expression,text)

for i in pattern2:
    print(i,end='')
    
    
    
### Resources 

- The excellent [Regex Playground](https://leaverou.github.io/regexplained/) of Lea Verou 
- The Video tutorials 

That's it for now. If I missed something let me know in the comments! 



