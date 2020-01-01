---
layout: post
title:  "What I learned from doing the Advent of Code 2019"
date:   2019-12-27
categories: iOS, developer
comments: true
published: true
---

![AoC Image](/assets/img/aoc/aoc0.png)


The [Advent of code 2019](https://adventofcode.com) in December 2019 has been a great experience.  

At the beginning of the month, I had to study hard for the IHK German Chamber Of Commerce Software developer exams. After passing those I was able to focus on different things again. To spend more time just writing code and algorithms in the language of my choice has been a great way to relax and have some fun!  

I enjoyed the challenges and especially the realisations that came with them. The puzzles were not easy for me. I cannot believe 100 people a day could manage to solve those in less than one hour.     
I loved the Reddit with the discussions and the poems!  
Not only people get to solve these much quicker than me but they manage to write a poem too. I thought this was wonderful, also I enjoyed to see that people used so many different programming languages to solve the challenges, from Bash, to Go, to Excel, even ARMv7-M Assembly!  

It is incredibly inspiring to see so many skills in actions and look at each other code, even if I do not understand most of it.  
With time I found two other developers using Swift and the solutions were implemented using packages and templates, allowing the code to be run in Terminal on Mac or Linux. I thought this was interesting because Swift is open source and I still rely too much on the Apple platform.     

This blog article is still in progress and will be for a while, because at the time of writing I did not finish the [Advent of code 2019](https://adventofcode.com). I managed to get to day 15 and then life got in the way.  

I am just not fast enough I guess. In 2020 I will put all my energies to prepare myself for hopefully a new job as a Software developer. Priority are editing my Website, write my CV and apply for jobs. I will put the challenges aside for the moment being!

#### What can go wrong using the Swift Playgrounds on Xcode?  

My programming language of choice is Swift and I thought the Xcode Playgrounds would be ideal for this. I did not know what would expect me haha!
At the end of the article below, I will explain more in detail the pro and contra of using the playgrounds for the challenges.

I collected all the challenges in one big playground with multiple pages and published it on [Github](https://github.com/multitudes/Advent-of-Code-2019) to document my journey.

Xcode playground can insert markdown and create a nice layout to introduce and describe the challenges and explain the code. They are similar to the Notebooks in Python, and it seemed to be a great feature and a bonus. As seen in the images this is an example of markdown rendering and navigation in the playgrounds. I assigned a shortcut to go from the editing mode to the rendered mode.  

![AoC Image](/assets/img/aoc/markdown0.png)
![AoC Image](/assets/img/aoc/markdown1.png)

Many WWDC scholarships submission are done with the playgrounds and its use is also actively encouraged by Apple.
Swift is a modern language said to be as fast as C and offer many nice features like functional programming. Sounds too good to be true! Let's get started!

### Day 1

This was just to get the party going.   

The leaderboards have been unlocked in 4 minutes 12 seconds, which mean it took so long for the first person to get to the solution.   
Especially for people starting doing the challenges to learn a new language, the first day is helping to get the system ready, to get comfortable doing all basic operations required by the later challenges like reading and saving files from a disk, display solution, print to screen etc.

Not difficult at all but it took a long time for me to understand how certain things in Playground works.    

For instance, where do I put the input file? In the Sources or Resources folder? Not a trivial question. The Sources folder is for the source code, but it would work for any other resources too. However, the correct way is to put the input.txt file for the puzzle in Ressources! The Sources folder is for the code. Swift files will not be recognized if put in the wrong folder. This I learned!

![AoC Image](/assets/img/aoc/sourceFolder.png)

### Day 2: Meet the IntCode Computer  
  
The IntCode Computer is at the heart of many AoC 2019 challenges.   

It starts on day 2:

> An Intcode program is a list of integers separated by commas (like 1,0,0,3,99). To run one, start by looking at the first integer (called position 0). Here, you will find an opcode - either 1, 2, or 99. The opcode indicates what to do; for example, 99 means that the program is finished and should immediately halt. Encountering an unknown opcode means something went wrong.
For example, suppose you have the following program:
1,9,10,3,2,3,11,0,99,30,40,50
The first four integers, 1,9,10,3, are at positions 0, 1, 2, and 3. Together, they represent the first opcode (1, addition), the positions of the two inputs (9 and 10), and the position of the output (3). To handle this opcode, you first need to get the values at the input positions: position 9 contains 30, and position 10 contains 40. Add these numbers together to get 70. Then, store this value at the output position; here, the output position (3) is at position 3, so it overwrites itself. 

This challenge has been continued in Day 5 where we got more opcodes and in day 7 where we had to use the IntCode Computer to activate out thrusters to reach Santa on time:

>The Elves have sent you some Amplifier Controller Software (your puzzle input), a program that should run on your existing Intcode computer. Each amplifier will need to run a copy of the program.

And finally in day 9 came what resulted for many to be a watershed moment in the advent of code:

>Your existing Intcode computer is missing one key feature: it needs support for parameters in relative mode.
Parameters in mode 2, relative mode, behave very similarly to parameters in position mode: the parameter is interpreted as a position. Like position mode, parameters in relative mode can be read from or written to.
The important difference is that relative mode parameters don't count from address 0. Instead, they count from a value called the relative base. The relative base starts at 0.

This challenge somehow came as a shock and became a roadblock for me and many others like is to be seen on the [reddit forum](https://www.reddit.com/r/adventofcode/comments/e85b6d/2019_day_9_solutions/fa9e8av?utm_source=share&utm_medium=web2x) 

![Reddit Post Image](/assets/img/aoc/aoc1.png)

The first big problem came on the day 9 part 1 challenge.  
Many forgot to implement the relative mode on the third parameter, which had been mostly implicitly left out till now.   
This would give ‘203’ as output. 
I thought there is an element of genius in how these challenges are made. :) 

I found out and corrected the code. Everything was working correctly now.   
Perhaps not as elegantly as I wanted but still, this is my first AoC and I am no professional developer after all. Every smaller test file with IntCode was working.. but part two got caught in an infinite loop or so I thought. Nobody else had this problem. I read and reread the challenge description including all possible hints on the AoC website and the Reddit. 

Especially this sentence below had me thinking for a long time.

>Part two does have a purpose. I'm not telling exactly what it is yet, but it's an entirely different kind of test than part 1 did. If you got the right answer, your Intcode implementation passed that test. If you got part 1, you should have gotten part 2 for free, but virtual machines are persnickety critters.

and 

> Once run, it will boost the sensors automatically, but it might take a few seconds to complete the operation on slower hardware.

A few seconds...? I have a mac mini 2018 with an i7 intel 6 cores... It cannot run for 10 minutes?  

I spent hours on this inserting more and more print statements (which ironically would just make my playground slower). I had a bad feeling. Part two would not give me any output and I could not find the bug.  I had a break from the IntCode!  

Desperation is a part of doing the challenges. In my case it turned out that the playgrounds as I was using them were too slow!  

## Day 3: Crossed Wires

The nice thing about this challenge is the understanding that came with using the right collection type in Swift.   
For this Sets were the best solution to be quick and efficient.   
At day 3 I started to refactor code and use a separate swift file for functions and structs in the Sources folder. 

## Day 4: Secure Container

Cryptography! Create a sequence of numbers and check how many meet the selected criteria. Good fun, I thought it would be easier then I had an "aha" moment. My solution was wrong. I had to think harder, and this is part of the fun :)
I printed the sequences to debug and could see that this slowed down the code quite a bit. I took out the print statements to see if the speed would improve.   
When writing the this article I actually went back and recorded this gif:

![Reddit Post Image](/assets/img/aoc/aocday4-slow.gif)

I did not realize at the time how bad this was.  I later understood this code would run instantaneously on Swift but not on the playground page...
But the worse was yet to come! 

## Day 5 - Sunny with a Chance of Asteroids

Again fun times with the IntCode computer!

## Day 6 - Universal Orbit Map

A classic linked lists problem 

## Day 7 - Amplification Circuit

Using the IntCode computer! It gets more and more obvious that who had already at the beginning a modular implementation of the computer will be at advantage! 

## Day 8: Space Image Format

This was neat and not too difficult.

## Day 9: Sensor Boost

Getting dirty!  
The new feature of the IntCode Computer!
> Your existing Intcode computer is missing one key feature: it needs support for parameters in relative mode.

This will bring some havoc :)


## Day 10

This challenge incidentally had a great learning effect on me. 
I had to stop and learn more about angles and radiants including the atan2() function! Great stuff and honestly not trivial, but I am happy that I understood now how to reverse the direction and calculate the angles of my laser beam to destroy those asteroids.  


## Day 11

Day 11 had me using the IntCode computer to manoeuvre a Hull painting robot. It worked! and that made me happy for the day!

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
This set of initial positions takes 4686774924 steps before it repeats a previous state! You might need to find a more efficient way to simulate the universe.

Part 2 of the challenge went into a loop again. All smaller test position has been debugged, the code seemed correct. I spent days on it. Xmas eve was in between so I stopped worrying and had a break. Eventually, after Xmas, I had a go at it again. Again I looked in Reddit for hints. The solution, which again was pure genius and I would probably have missed it, consists of calculating every axe independently, calculate the number of steps for it to go into the original position and velocity, then check the next axe and the next. The result is then the lowest common multiplicator or LCM of the three orbits!
I did this but the third orbit would just go on forever. I thought this is wrong.
I was growing increasingly frustrated. I thought this is the end of my challenges. I spent hours on it.
Until I left it running and made a coffee, then had a phone call. And when I came back the answer was staring at me:

>376243355967784

Beautiful but how is that possible? I finally googled specifically for "How slow are playgrounds compared to Swift?"
I found this enlightening answer on SO [recursive-algorithm-is-much-slower-in-playgrounds](https://stackoverflow.com/questions/55303853/recursive-algorithm-is-much-slower-in-playgrounds-1-minute-than-xcode-0-1-sec) and [swift-playground-execution-speed](https://stackoverflow.com/a/47542545/9497800)

Of course, the most performant way is to make all the performance-critical code in a Swift file inside the Sources folder in the playground, but I never imagined this would make such a big difference! 

This below is another example of how the Playgrounds can be unexpectedly quirky!

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



# Get more Performance!

-Put all your classes and structs in a swift or a few swift files and add them to the sources folder. All the classes and structs need to be marked public or the main code will not see them. This will speed up the performance considerably.
- Use fewer print statements.
- Use macOS playgrounds (there an option for that in the inspector)

## The disadvantages to using Xcode Playgrounds for Swift 

- Once you put your classes and structs in sources there is a message that you will get all the time like: "... is inaccessible due to internal protection level". This informs you that you need to make every single property and methods public. That's a lot of extra typing because the structs will need a public initializer. Usually, you would get one for free, well they do need one now. 
- Putting the code in the source makes it very slow to debug, the playground needs minutes(!) to understand that you made a change in a Swift file in sources, or that a struct that was in the main file previously, is now in the Sources folder.
- I had to restart Xcode a lot doing the above. Xcode again needs quite a long time to understand that the permission has been changed from internal to public.
- Playgrounds do not have debuggers. An easy option is to use print statements and these make your code slow.

