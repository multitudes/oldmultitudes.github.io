---
layout: post
title:  "Elements of Functional programming in Swift"
date:   2019-05-23
categories: iOS, developer
comments: true
published: false
---


<div class="message">
"Any fool can write code that a computer can understand, but good programmers write code that humans can understand"
<br><cite>Martin Fowler</cite>
</div>

in this talk I want to try and

give you some real quick wins quick wins

because sometimes you get words like

monads and funk doors and applicative

thrown around and it can seem very dry

and very academic and not for you when

it really is so this concept of quick

wins I have shamelessly stolen from an

ex Apple engineer called and EEMA to

Shack and the idea is he talks about

lightweight encounters you dip in get

some quick wins and run away for it gets

too hard.


what makes good functional code one of

them is we rely very strongly on

immutability we like using constants

everywhere and of course swift and

forces is for us you try and change a

constant you get nothing at all

we haven't compiled

good functional code avoids state at all

those little properties you store away

settings and so forth it might start

like this but after a few months if not

years what you normally get a much messy

situation so good functional code avoid

states you pass values into a function

change them inside the function and

return new values you avoid external

stuff and of course this makes a code

significantly easier to test you know

that function a will always return one

two three for the same values every

single time regardless of any properties

you might be using good functional code

is composable you write small functions

that do one maybe two things then

combine together to make bigger

functions like Lego bricks but most

importantly good functional code allows

us to express our intent clearly it

clarifies our intent use your quote

stolen from xavier soto from twitch he

says it allows us to express what we

want to achieve rather than how it's

implemented smart man now enough intro

let's get to the code somethings map map

works great on collections and optionals

and we're starting easy collections okay

where does it transform stuff values

come in get transformed by a closure

rights and emitted as transformed values

r example one two three four map can

double that to be two four six eight

nice and easy

play some English words camping parking

in weekend we can say hey map make that

French

as Kumar said English is just French

badly pronounced map could even try and

make olympic marseille it's a good

football team but probably not now as an

example imagine a function which accepts

an array of names John Paul George and

Ringo the onus function to transform

those names into the links of host names

nice and simple we know that John has

four Paul has four George has six Ringo

has five array of strings in int array

of counts back you're doing that

declaratively you would say length of

string string array going in return int

array make a new empty int array loop

over the strings add white count to the

intr a and the loop and return the

results that is your declarative

function throw a comparator throughout

that functionally you would say step one

get rid of all that code step two you'd

write strings dot map dollar zero dot

count step three well there is no step

three that's all your code now and the

best bit is the function signature

hasn't changed all the code that calls

this function can be as nasty as it is

right now this code can be improved so

you can go ahead and chisel away at your

bad code base and improve it as you go

now if you don't use close as much

dollar zero just means this element

being passed in so John then Paul then

George then Ringo now this code is

shorter of course this code shorter but

that's not the real win here okay this

code is immutable that variable integer

array done but it also clarifies what

we're trying to do are intense clear

when you call map on a sequence like I

did there

it must transform all the items in there

you can't bail out partway through four

laughs internally to Swift it looks a

bit like this I've simplified its slight

this is map internally to Swift and

standard library map transforms some

generic thing or turned the generic

array of T create a new empty array of T

loops over the items itself and then

transforms your item puts into the

return value then ends a loop returns

turn value and returns a function that's

exactly the same code you would

written except now it's Swift's problem

now it's Ben's problem through Apple to

let that work better which means they

can optimize that over time to be better

and faster and you don't care your code

just improves you can map all sorts of

things here's an integer array 108 85 we

could say map that into strings your

score was dollar 0 your score 100 score

80 or 85 we could have yeah I'm Strama

cram come on whist applause my friend

che

thank you we can say I want to map that

to be uppercase and I'll just return

those things upper case we could say his

array of doubles two four nine and

sixteen we could pass that straight to

the square root function and get back

two three four map all sorts of things

and actually earlier Daniel Steinberg

gave me a lovely analogy for how map

works similar to you I've used in UIKit

we're very comfortably the idea of

saying here's a view I want you to

animate with a 5 second duration from

where you are down to the bottom right

corner and it will do so we haven't

going to tell it exactly where to be in

every frame of the animation we just say

the start point and the end point the

transformation and let you Ike it sort

it out very similar map that is map move

on flat map in a smaller type compact

map it's being renamed because of course

you know Swift or R in Swift for one

which is command next code and I put

three years ago it's now compact map

this precise you just I'm talking about

but it's very similar to map please

already map and your brain you think

you've more the transformation happening

here of course there is but a second

part the flat / compact part it does

something really cool after the map

transformation completes it will unwrap

your optionals then throw away any Nils

for you and nil occurs in all sorts of

places and Swift

so if loves nil X variable initializes

or try question mark or conditional

typecast and so forth all of these when

they fail return nil so when you say

create the integer from this string

number 5 a will actually be an optional

integer because you may have said not as

your number and of course the French

don't you anyway you get nil back for

that

so nil brilliant good food to flatmap

let's see that the flatmap thinks of

that we can say here's an array of one

five fish deer flatmap please put that

through the initializer and what get

back is this numbers array will be an

int array not optionality here

whatsoever it's a real int array it'll

work out like this we have one five fish

it goes through the International Iser

which is available it comes back as

optional one optional five Neil the

flattening they're compacting part kicks

off unwraps the optionals tosses away

the nails out comes one five beautiful

so anywhere you have failed but

initialized you should be thinking flat

map for example got an array of strings

that might be URLs might not be let's

find out try and make your else out of

them for lucky there we go

it fails black my posters my way an

array of UI views

some of which might be your image use

great let's do a conditional typecast

the ones you get back our image juice

you can even just do this there's no

transformation happening here

you're just saying please give me your

lovely compacting behavior please under

optionals and toss away the nails that's

black map now both of these things work

on optionals too you can do an optional

map and an optional flat map and they

work in slightly different ways i think

you an option of being a box map will

open the box

it'll extract the contents of a box some

the teller and it of course transform

that into vast amounts of money right

now for the rioters and then it will put

that thing back in the box so it rear a

pit back in and optional again get an

optional you end up with an optional so

in code if you imagine a method like

this get user ID keep an ID number 97 if

it exists you get a string back if it

doesn't get nil back there's an optional

string return value we can pass that

thing through map and if name is bill

nothing happens you get back nil

immediately but if name is not nil

you'll get high user name hi jean-pierre

and then you can say go ahead and print

the greeting nil coalescing unknown user

now it's the same thing declaratively

you might say the same court start then

an empty constant do a quick unwrap put

it into the variable the end of an else

block lucky there we go

unknown user anything else and then

pronounce routing crazy there we go

now easy enough but what if what's in

the box isn't what you thought you open

the box out comes your prize transform

to big cash but this time it is optional

what happens then find out so here we

have an optional string containing five

we say okay let's try and map that to an

integer what type is result spoiler it

is not an integer it's not even an

optional integer what you've got here is

the lesser known and completely never

wanted optional optional integer which

really screws with your head no one

wants to see these things now when we

said map what we meant to say really was

flat map and now result will be a

regular optional int that we feel much

more comfortable with you see when you

call map or an optional and your

transformation closure

returns an optional map just put them

together you get an optional optional

flat map is able to say it's the same

container let's join them together it

can turn that into a single optional

either the whole thing is there or the

whole thing is not there so your

transformation closure returns an

optional use flat map move on filter you

like coffee and France don't you still

Turing filtering is where you can say

here is a condition I want to check pass

this collection or sequence through this

filter and see what comes out for

example I have an array of red and blue

boxes I have a filter looking for blue

boxes I can now say run it through the

Reds are thrown away balloons come back

that's my return value so time for some

examples and let's of course play to the

crowd a little bit let goodwine equals

wind-up filter origins France let band

equals player stop filter has a prefix

Kevin the band he'll called Kevin from

the thing great you can tilt whatever

you like let's filter these numbers base

where they are odd or not using modulus

and there's so many more Swift packed

these lovely functional functions you

can call on I love the first method this

will find the first score over 85 like

that you've got array of numbers 9 5 3 5

and your cat Hoff and they appear

trivial you can put it through map make

an array of tuples so it'll produce an

array like this nine one five one two

three one five one then swift for

there's a new dictionary initializer it

will treat that array of tuples as key

value pairs so keys one values one keys

three values one and so forth it's

called unique and keys with and when it

finds a collision in the keys like it

will four five and five it'll add the

one on the one together so wrote result

will be nine appears once five appears

twice three appears once it's trivial to

do there's a classic one you'll see on

so many talks how to add an array of

numbers using reduce and plus it's shown

so many times because it's beautiful it

shows you how swift just totally blurs

the lines between functions methods and

operators and closures one big thing of

beautifulness and swift you can even

take it's ready to more french you can

even take non-functional things you know

already and apply them isn't of rain we

wait the answer you can say exactly

saying we you know this there's a

contains method and arrays you know this

and there's a stream contains we can say

marathon said we look at saying we we

put the two together you can now say

here's my array of words we web beyond

suit here's my string and then say yes

doc contains where replied or contains

do any of those words appear in that

string done now there are some

challenges to switching to a more

functional approach of course there are

first up muscle memory we sit down at

your desk ready to face the same

problems we face before you naturally

reach for the same solutions you use

before switching to map or flat map or

reduce or whatever you want to do is a

mental jump but it's worth it second up

some hope to tell you Swift

is not a functional language or a true

functional language and the you know

I've semantics it's functional its

protocol oriented it's the clarity of

its object-oriented it's good but one of

the biggest ones is that state is

comfortable we like storing things in

properties right and then referring to

them later on so getting away from that

get into what you might call a pure

function where you only refer to the

values inside the function takes a work

and that's okay so let's wrap up first

up I hope you learn soon you I hope you

impressed by my french suck it up you

weren't you scared

I did try and keep it as simple as

possible quite as applicable as possible

and thirdly I hope that tomorrow you can

go back to your desk and apply what

you've learned she just learned

functional program look at happen she is

right that could be you merci beaucoup


### Sources:
[Paul Hudson - Elements of Functional Programming](https://www.dotconferences.com/2018/01/paul-hudson-elements-of-functional-programming)
[Teaching Swift at Scale - Paul Hudson](https://vimeo.com/291590798)
[SwiftConf '18 - Paul Hudson: Mastering iOS Animation](https://www.youtube.com/watch?time_continue=41&v=_4McEnarqNc)
[https://learntalks.com/tag/paul-hudson/](https://learntalks.com/tag/paul-hudson/)


<hr>

[^1]: What?