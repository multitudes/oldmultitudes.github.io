---
layout: post
title:  "What I learned from the AoC for Swift Playgrounds"
date:   2019-12-27
categories: iOS, developer
comments: true
published: true
---

This blog article is still in progress because at the time of writing I did not finish the [Advent of code 2019](https://adventofcode.com). 
I wanted to do the challenges with swift and I thought the Xcode Playgrounds would be ideal for this. I would collect all challenges in one big playground with multiple pages and publish it on [Github](https://github.com/multitudes/Advent-of-Code-2019).

After all the possibility to insert markdown and create a nice layout to explain the code seemed a great feature, and many WWDC scholarships submission are done with the playgrounds and it is also actively encouraged by Apple.
Swift is a modern language said to be as fast as C and offer many nice features like functional programming. 
I thought about writing about my experiences doing the AoC but kept procrastinating. I started quite late doing the challenges and could not catch up fast enough to finish them by the 25th. 
Today is the 27th December and I am still on day 13! However, I had a nagging bug on the IntCode Computer on board of my spaceship. The IntCode Computer started building itself on day 2 where we had to decode an easy sequence of instructions.

## The IntCode Computer

The IntCode is at the heart of many AoC 2019 challenges. It starts at day 2: 

> An Intcode program is a list of integers separated by commas (like 1,0,0,3,99). To run one, start by looking at the first integer (called position 0). Here, you will find an opcode - either 1, 2, or 99. The opcode indicates what to do; for example, 99 means that the program is finished and should immediately halt. Encountering an unknown opcode means something went wrong.
For example, suppose you have the following program:
1,9,10,3,2,3,11,0,99,30,40,50
The first four integers, 1,9,10,3, are at positions 0, 1, 2, and 3. Together, they represent the first opcode (1, addition), the positions of the two inputs (9 and 10), and the position of the output (3). To handle this opcode, you first need to get the values at the input positions: position 9 contains 30, and position 10 contains 40. Add these numbers together to get 70. Then, store this value at the output position; here, the output position (3) is at position 3, so it overwrites itself. 

This challenge has been continued in Day 5 where we got more opcodes and in day 7 where we had to use the IntCode Computer to activate out thrusters to reach Santa on time:

>The Elves have sent you some Amplifier Controller Software (your puzzle input), a program that should run on your existing Intcode computer. Each amplifier will need to run a copy of the program.

And finally in day 9:

>Your existing Intcode computer is missing one key feature: it needs support for parameters in relative mode.
Parameters in mode 2, relative mode, behave very similarly to parameters in position mode: the parameter is interpreted as a position. Like position mode, parameters in relative mode can be read from or written to.
The important difference is that relative mode parameters don't count from address 0. Instead, they count from a value called the relative base. The relative base starts at 0.

This came as a shock, and became a road block for me and many others like is to be seen on the [reddit forum](https://www.reddit.com/r/adventofcode/comments/e85b6d/2019_day_9_solutions/fa9e8av?utm_source=share&utm_medium=web2x) 

![Reddit Post Image](/assets/img/aoc/aoc1)

The first problem on day 9, many forgot to implement the relative mode on the third parameter which had been mostly implicitly left out till now. This would give '203' as output. I thought there is an element of genius in how these challenges are made. I found out and corrected the code. Everything was working correctly now, Perhaps not as elegantly as I wanted but still, this is my first aoc and I am no professional developer after all.
Every smaller test file with IntCode was working..  but the part two got caught in an infinite loop or so I thought.
Nobody else had this problem. I read and reread the challenge description including all possible hints on the aoc website and the reddits. This sentence had me thinking for a long time

>Part two does have a purpose. I'm not telling exactly what it is yet, but it's an entirely different kind of test than part 1 did. If you got the right answer, your Intcode implementation passed that test. If you got part 1, you should have gotten part 2 for free, but virtual machines are persnickety critters.

and 

> Once run, it will boost the sensors automatically, but it might take a few seconds to complete the operation on slower hardware.

A few seconds.. I have a mac mini 2018 with an i7 intel 6 cores...  It cannot run for 10 minutes? 

I spent hours on this inserting more and more print statements (which ironically would just make my playground more slow).

I had really a bad feeling. Part two would not give me any output and I could not find the bug.

I had a break from the IntCode and did the day 10 which incidentally had a great learning effect on me to get to know more about angles and radiants including the atan2 function!
Day 11 had me using the IntCode computer to manoever a Hull painting robot. It worked!

## Day 12

>The space near Jupiter is not a very safe place; you need to be careful of a big distracting red spot, extreme radiation, and a whole lot of moons swirling around. You decide to start by tracking the four largest moons: Io, Europa, Ganymede, and Callisto.
After a brief scan, you calculate the position of each moon (your puzzle input). You just need to simulate their motion so you can avoid them.
Each moon has a 3-dimensional position (x, y, and z) and a 3-dimensional velocity. The position of each moon is given in your scan; the x, y, and z velocity of each moon starts at 0.
Simulate the motion of the moons in time steps. Within each time step, first update the velocity of every moon by applying gravity. Then, once all moons' velocities have been updated, update the position of every moon by applying velocity. Time progresses by one step once all of the positions are updated.

Arriving at day 12 I had to cross a till now invisible? to me and unforeseen barrier with my Xcode Playgrounds.
The challenge is about performant code!

>Determine the number of steps that must occur before all of the moons' positions and velocities exactly match a previous point in time.
For example, the first example above takes 2772 steps before they exactly match a previous point in time; it eventually returns to the initial state.
Of course, the universe might last for a very long time before repeating. 
This set of initial positions takes 4686774924 steps before it repeats a previous state! Clearly, you might need to find a more efficient way to simulate the universe.

Part 2 of the challenge went into a loop again. All smaller test position have been debugged, the code seemed correct. I spent days on it. Xmas eve was in between so I stopped worrying and had a break. Eventually after Xmas I had a go at it again. Again I looked in Reddit for hints. The solution, which again was pure genius and I would probably have missed it, consists of calculating every axe indipendently, calculate the number of steps for it to go into the original position and velocity, then check the next axe and the next. The result is then the lowest common multiplicator or LCM of the three orbits!
I did this but the third orbit would jut go on forever. I thought this is wrong.
I was growing increasily frustrated. I thought this is the end of my challenges. I spent hours on it.
Until I left it running and made a coffee, then had a phone call. And when I came back the answer was staring at me:

>376243355967784

Beautiful but how is that possible? I finally googled specifically for "How slow are playgrounds compared to Swift?""
I found this enlightening answer on SO [recursive-algorithm-is-much-slower-in-playgrounds](https://stackoverflow.com/questions/55303853/recursive-algorithm-is-much-slower-in-playgrounds-1-minute-than-xcode-0-1-sec) and [swift-playground-execution-speed](https://stackoverflow.com/a/47542545/9497800)

Playgrounds are slow!

The most performant way is to make all the performance critical code in a .swift file inside the Sources folder in the playground. Note: In order to use the functions, classes, properties and methods from the Sources folder you have to mark them public. If you want to subclass a class it has to be marked open.


``` swift
var count = 0
for i in 0..<1_000_000_000 {
    (count += 1) // try to execute the code with or without the parenthesis! 🤯
    if count % 100_000 == 0 {
        // print only every 100_000th loop iteration
        print(count)
    }
}

```

Without the parenthesis: about 10.000 loop iterations per second
With parenthesis: about 10.000.000 loop iterations per second !!!


## The disadvantages to use Xcode Playgrounds for Swift 

to be continued
