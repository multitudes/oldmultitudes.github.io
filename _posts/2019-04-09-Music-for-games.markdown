---
layout: post
title:  "Music for Games - About Generative and Adaptive music"
date:   2010-04-09 10:41:47 +0100
categories: Music for Games, Generative music, Adaptive music
comments: true
published: true
---
<div class="message">
"Stop thinking about art works as objects, and start thinking about them as triggers for experiences" 
<br><cite>Brian Eno</cite>
</div>

![image](/assets/img/idalab-meetup.jpg)

### The Melodrive Meetup at Adalab 
Last week I attended a Meetup with the founder of [Melodrive](https://melodrive.com) at [Adalab](https://ada.com/team/) and I learned a lot about music for games in a very short time. 
Not only the meetup and the presentation about adaptive music in videogames by Valerio Velardo has been very entertaining (he even played Eric Satie on a real Piano in the room to explain his point of how complex the task of teaching a machine about music would be) but very inspiring too and gave me input to research more for myself.
Before and after going to the meetup I researched a bit about generative and adaptive music for games. 
I want to share some of my research in this blog post.

### Melodrive

Melodrive is a startup based in Berlin and specialized in AI, audio, music technology and video games. 
They created the Melodrive Indie, a plugin for Unity that automatically generates music for video games in realtime. 
Artificial intelligence is the buzzword but really Melodrive is using Symbolic AI, which is not the AI of Big Neural Networks we all know. 
In Symbolic AI there is a fair amount of work involved in making the computer to behave as an intelligent creature and expert musician. 
Indeed the computer is pre programmed in Music Theory and uses a randomized seed to create new tracks on the fly. Still the computer does not know about Music as we hear it. 
All the constraints in the system are man made and it is not a small task. 
However as far as I understood the system is not learning more from the game as it progresses.
Music is such a difficult topic actually. 
To make a computer produce music we like, or that it is suitable to our emotions, we would need lots of labelled data, and this is hard to get. 
Not only this but how do you label this data? Not easy , since everyone of us has different ideas about music they like, what kind of music they perceive as inspiring and so on.
A very interesting idea is to make music adaptive to the gameplay. 
To do this on unity you first define a few things.See also the tutorials on [youtube](https://www.youtube.com/watch?v=fQeoPf9ivL4) for a quick overview.
First of all there are the concepts of "Valence" and "Arousal". 
With a cartesial coordinates in a 2 dimensional space we can define a state of emotion with a vector. The valence defines the positive or negative emotion. 
So Arousal defines the intensity of the emotion, tender or strong. Neutral for instance will have the coordinates "zero, zero" in the two dimensional space.
With this knowledge we use this in our Unity code accordingly. 
Example, the amount of arousal can be proportional to the distance from our character to a dangerous situation. We can have a sad battle versus a happy one! 
I think this is quite an interesting concept.
With Melodrive you kinda choose the style of music being played in your game or application. 
This has to be coded in Unity. Melodrive is a free download and quite an interesting possibility to have generative music in your game. 

### Nintendo

Nintendo has been is one of my favorite platform for gaming and they always had killer soundtracks.
They are in my eyes also the pioneers of adaptive music for videogames already in the very beginnings.
I looked up a few interviews with the legendary Koji Kondo. I just wonder which software they used for these soundtrack though. 
There is a lot of thinking and designing involved. Making music that always sound fresh is not easy!

> We also want to make sure that players,[...] don’t get tired of the music. 
We have all the different tracks – the base track, the piano, the drums – which we try to do some interesting things with using our recent technology. 
Whether it’s lowering or increasing volume, or bringing them in and out of these separate tracks, we always want to make sure the music sounds fresh and new so the players never get tired of hearing it.

> Ask Nintendo sound composer Koji Kondo what his favorite game-biz memory is, and the answer comes pretty quickly. 
"A lot of people remember how Paul McCartney invited Shigeru Miyamoto to a concert when he played in Japan," he said in a Famitsu interview this week, "but Miyamoto actually brought me along to that so he could introduce me as the 'Mario music guy.' 
Paul and his wife Linda responded by singing the melody to me -- 'Oh, the da da dah da da dah dah guy!' 
I'd always been a fan of the Beatles, so the fact that they immediately recalled the melody was a really proud moment for me."
Unlike CDs and film soundtracks, game music is special because it changes in realtime," he commented. "The sound needs to work with the game. 
That's why the music in Mario speeds up when you're about to run out of time. We didn't have enough space in the first game to create a whole new tune for that situation, so we just sped up the tempo instead.
<div>
<cite>Koji Kondo - Nintendo legendary Mario and Zelda composer </cite>
</div>


### Spore and Brian Eno

Speaking about music in videogames we should mention Spore.

> Spore is a 2008 life simulation real-time strategy developed by Maxis and designed by Will Wright, and was released for Microsoft Windows and Mac OS X.
development of a species from its beginnings as a microscopic organism, through development as an intelligent and social creature, to interstellar exploration as a spacefaring culture.
<br><cite>From Wikipedia</cite>

It is a brilliant example of adaptive music generation. 
The music changes all the time depending of the stages of the game and Brian Eno created the generative music together with Peter Chilvers.
Now, for me having Brian Eno collaborating for the music in this game is a very big deal.
I have been a long time fan of his ambient music, especially "Apollo" and "Music for Airports".
Generative music is a term which has been created by Brian Eno, to describe music that is ever-different and changing, and that is created by a system.
He developed an app for the iPhone and iPod Touch together in 2008 developed with Peter Chilvers: [Bloom](http://www.generativemusic.com/bloom.html)

### Pure Data

> Pure data is an open source visual programming language for multimedia that runs on anything from personal computers to embedded devices (ie Raspberry Pi) and smartphones (via libpd, DroidParty (Android), and PdParty (iOS). It is a major branch of the family of patcher programming languages known as Max (Max/FTS, ISPW Max, Max/MSP, etc), originally developed by Miller Puckette at IRCAM.
<br><cite>Pure Data website</cite>

![Pure Data Patch example](https://pbs.twimg.com/media/CrD0c94UAAAKiIs.png)

The sounds of the Spore's soundtrack are created with Pure data.
I am honestly impressed by the sounds created by the Pure Data application. 
Very beautiful. 
There is only the danger to be tied artistically to a particular this sound which will be immediately recognizable to listener who know it already. 
Personally I love it, but dont have experiance with the package at the moment so I cannot say more about it.

### Generative Music in your Browser. The Web Audio Platform

Making ambient and minimal ambient and generative music is possibile in the browser too.
The Web Audio API is widely supported in browser and allows generative music to be created in your browser. I think this is quite exciting.
I came across to this project of [Alex Bainter](https://generative.fm) which I quite liked. I did enjoy his blog post as well :[Introduction to Generative Music](https://medium.com/@metalex9/introduction-to-generative-music-91e00e4dba11).

I see here a lot of potential and inspiration to use generative and adaptive music in a variety of situation, and this has been quite a big introduction for me in such a short time and hope to take it further, especially now getting more into iphone and iOS development.

<!-- 
The Drake equation is a probabilistic argument used to estimate the number of active, communicative extraterrestrial civilizations in the Milky Way galaxy.
 -->

PS Check this too! Great music: [Aisatsana by Aphex Twin](https://www.youtube.com/watch?v=bj30yfuXKy4)

That's it for now. If I missed something let me know in the comments! 



sources:

[IGN - How Mario Maker Mixes Music With Level Creation](https://www.ign.com/articles/2014/12/08/how-mario-maker-mixes-music-with-level-creation)
[Chatting with Koji Kondo - Nintendo Minute](https://www.youtube.com/watch?v=3WsP4lnFq9w&t=3m25s)
[Koji Kondo on the Nintendo approach to game soundtracks.](https://web.archive.org/web/20150929062439/http://www.1up.com/news/mario-music)
[wiki - Koji kondo](https://en.wikipedia.org/wiki/Koji_Kondo)
[David Wise](http://davidwise.co.uk)
[A Composer's Guide to Game Music](https://mitpress.mit.edu/books/composers-guide-game-music)

[Spore, birth of a game](https://www.ted.com/talks/will_wright_makes_toys_that_make_worlds?language=en)
[Drake's Equation](https://en.wikipedia.org/wiki/Drake_equation)
[Spore's Development](https://en.wikipedia.org/wiki/Development_of_Spore)

[Generative.fm](https://generative.fm/about)
[Learning Web Audio by Recreating The Works of Steve Reich and Brian Eno](https://teropa.info/blog/2016/07/28/javascript-systems-music.html)

[Pure Data](https://en.wikipedia.org/wiki/Pure_Data)

[Brian Eno, with Wright on Spore and Generative Systems, Sound, and Paintings](http://cdm.link/2007/06/brian-eno-with-wright-on-spore-and-generative-systems-sound-and-paintings/)

[Will Wright and Brian Eno - Spore Creature Demo](https://www.youtube.com/watch?v=8PXiNNXUUF8)
[Bloom](http://www.generativemusic.com/bloom.html)
[Comparison of audio synthesis environments](https://en.wikipedia.org/wiki/Comparison_of_audio_synthesis_environments)
<br>