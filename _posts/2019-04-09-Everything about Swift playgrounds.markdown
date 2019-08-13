---
layout: post
title:  "Everything about Swift playgrounds"
date:   2001-06-15
categories: iOS, developer
comments: true
published: true
---
# achtung.. still a draft :)

## Why Playgrounds?

I love the fact that every time I have a new coding idea I can jump right into a playground to try it out.  

When you first open a playground, Xcode shows you the standard editor.

// pic

What is unique about this editor when you're in a playground is the result sidebar on the right hands side displaying the result of each expression in your code. You also have the ability to add these results as inline results.  This is done by selecting the rectangular button beside your result in the result sidebar.  
This will then show your result inline with your Swift Code.  

### Let's take a look at the assistant editor mode.  
You can visualize your results in more detail by using a live view.  
First you need to import PlaygroundSupport.  
PlaygroundSupport is a framework provided by Xcode to allow playgrounds to interact with Xcode, including support for showing live views.  
You import this playground support framework so you can use its API.  
Once you've created a viewController using the standard UIKit or AppKit APIs, you need to hand it over to the PlaygroundSupport framework.  
You do this by setting the Live View property of the current playground page to your viewController.  
This signals to Xcode that it should show your viewController in the assistant editor.  



### Multiple pages

Up to this point we treated a playground as a single location, but playgrounds can contain multiple pages, each with their own markup and code.
To create a new playground page, select the playground and then open the file menu.
Select New, then Playground Page.  
You could also create a playground page by control clicking on the playground and then selecting New Playground Page.  
You can create links in your markup, which navigate between pages.  
To go to the previous page, you can create a link where the destination is @previous.
To go to the next page you can create a link where the destination is @next.
Finally, if you want to navigate to a specific page, you create a link where the destination is the file name for that page without the extension and by replacing any spaces or special characters with their percent in coded form.

### Adding Swift files to the sources folder

You can also imbed some additional content to make you playgrounds even more powerful.
You can add additional Swift files to the sources folder, which is at the top level of the playground.
Each page also has its own sources folder.
Sources are compiled as separate modules where they are automatically imported where visible so you don't have to handle import statements.
Since these are compiled as separate modules, you can use access control to control what is exported from your axillary sources.
Anything you want to use as your main playground source should be marked as Public.
A great example of things to put into the sources folder is helper code such as classes or extensions that are outside of the main playground.

### Adding other resources

Playgrounds can also contain other resources.  
Resources are any other file that you'd like to use in your playground such as images, audio, video, storyboards, and ZIPs.
Just like sources, there's a resources folder at the top level of the playground as well as for each page.
You can use these resources that you've added to your playground both in your markup and code.
Similar to how you create a link in your playground, you can use this highlighted syntax to imbed an image in your markup.
You also specify alternate text describing the image along with hover title text that shows my pointer is over the image.
Both alternate text and hover title text can also be used for accessibility to benefit voiceover users.
And here we access the same imaging code using the standard UIImage or NSImage APIs.
Similarly, to images you can also imbed videos in your markup.
This is done by using a syntax similar for that images with additional support for specifying a poster image along with the width and height of the video.
For other resources that you want to access in code, such as this video, you can use the standard Bundle APIs for finding resources.
This example uses a URL for resource with extension API to ask the main bundle for URL for Myvideo.mp4.
 
 //:ToDo pic
 
Resources in your playground are automatically treated as resources of the main bundle.  

for more see the markup formatting [reference link below][1]
### 

Have you ever woken up with a great coding idea but then struggled to set it down before you reach your code editor? Perhaps it's your inbox that gets in the way or perhaps you haven't yet set up your project within Xcode.
Whether you're a beginner just getting started with Apple APIs, a seasoned engineer with a deadline, or a data scientist building machine learning models, I want to tell you that Xcode playgrounds are the fastest way to get started coding against Apple's APIs.
In Xcode 10, playgrounds are faster and more responsive than ever allowing you to execute your code in a step-by-step fashion.
First I'd like to get you familiar with a new UI for doing this.
If you're familiar with playgrounds, your eye should immediately jump to the blue line over the not line numbers.
There's a new play button which tracks your pointer.
A blue line over the line numbers mean these lines are ready to execute and when you click the Play button this means run all of the blue lines up to and including the one with the play button on it.
Let's see what that looks like.
There we go.
You can see just the first three lines of the playground are executed.
The results are visible on the right-hand side.
You can also see that the play button has now gone gray.
This indicates that these lines of code are no longer ready to execute.
You just executed them.
There's a second reason that they play button might be gray.
This means you're hovering over some code, which is not a top-level line of code.
This includes code inside function brackets and inside of fall loop.
If you wish to execute a fall loop you need to move your pointer to the closing brace where the play button will go blue then you'll be able to execute it.
There's also a great keyboard shortcut, Shift Return.
This is just like pressing Return at the end of typing a line of code, but it also means execute this line, and it move the cursor to the next line ready to write some more code.
Blue code also has a second interpretation.
It means code that it's safe to edit without resetting your playground.
Why is this important? If you edit code above the blue line this is modifying code that you've already executed.
So you'll have to resent your playground to take account of your changes.
When you edit code above the blue line, the playground resets automatically.
Sometimes you'll need to reset your playground manually and you can do this using the stop button in the Debug bar at the bottom of the screen.
So why run in a step-by-step fashion? Why have we added this feature? Firstly, executing just one more line is fast.
It's way faster than restarting a playground and waiting for it to catch up with your thoughts.
Secondly, it allows you to respond to live data.
Write a line of code, execute it, see what the results are, and this should lead you naturally to the next line of code to write.
And thirdly rerunning a playground every time can give you different values every time.
This can happen, for instance, if you're accessing a network resource or you're generating random numbers.
By executing step-by-step your data model stays stable and easier to understand.
So let's take a look at a simple example that you can try yourselves.
I like games.
I like card games and board games and computer games.
I even like writing games.
Now I'm not too hot at it so I like to keep my games small.
This is a really small game.
It's the game of roshambo.
It's the schoolyard game of rock, paper, scissors.
I've written the rules as a simple function check, which tells us if we've won.
I've also written a computer player, which simply makes one of the moves at random.
By executing step-by-step we can execute line six where the computer player plays and see what the result is before making our move.
In this case the computer player has played "rock" and we've played "paper".
Paper beats rock and we win the game.
This might sound a little bit like cheating, but it's an extremely powerful technique.
It's an extremely powerful technique when you're trying to learn a new and unfamiliar API or exploring a data structure whose types and values you don't yet know.
So that's a very simple example.
Now we're going to look at something a little bit more magical with a demo.
So we started off with one game, I'm going to move on to another.
This is the game of Tic-tac-toe.
I've already been working on this a little while.
I've built the game engine and I've made a first version of the UI.
I've moved all of that code aside into the auxiliary sources.
This gets it out of our way and allows us to focus on the next steps -- actually playing the game and refining the UI a little.
I'm also going to use a live view, but first let's look back at the blue control over the line numbers.
You can see that it tracks the mouse pointer.
So let's get started by loading the game board.
Let's rotate it so we can see it.
This is the Tic-tac-toe game board.
You can see I've been able to execute the first half of the playground and I've still got some lines left in the playground to execute.
These include my first move.
Let's run that.
There we go.
So you can see we're going to be playing the game in code and viewing the results with the live view.
Let's let the computer play and have a turn.
Few, that's great.
The computer player is completely random.
So it's just possible it's going to beat me today.
So I've shown you how we can execute some of the lines of code and then step-by-step execute lines of code which are already present in the playground.
But we can do more than that.
It's always safe to add new code at the end of a playground.
So let's make another move.
There we go.
Now, I can click the Play button to execute this line of code and I think now we'll let the computer have another go.
That's great.
[ Laughing ] You should notice a couple of things here.
Number one, in the beginning the board was flat.
I had to rotate it so it was in a position where we could view it.
As we execute more lines of code, it doesn't rotate back to its original position.
This is pretty good because I could write lines of code to rotate it to the correct position, but this would involve something called [inaudible], and I don't think I'm quite ready to learn that yet.
The second reason it's good is because if the computer player was allowed to play again, every time we executed new code it would effectively get a do-over, which would be a little unfair.
Let's finish this up.
I think I can take the game home from here.
Is that the right move? That's great.
You can see the game has highlighted my winning move by placing three red circles.
That's not too fancy.
I'm looking for something which really makes it feel like a celebration.
So I've been working on a new version of the UI.
In a traditional development environment, you would have to set up a complex harness to automatically play you deep into the game or whatever the API was you were using so that we could test out something that happened later on in the program.
But in a playground, because I'm able to execute step-by-step, I can play it manually to the end of the game and then write new lines of code to update whatever's going on at that point.
Let's do that now.
I've prepared a new effect for the end of the game using a particle system.
Let's use Shift Return to execute it.
Boom.
And that feels much more like a win.
So let's review what we've just seen.
By running step-by-step we can explore an idea a line at a time.
This enables us to have a conversation between code and data.
Every time we learn a new fact we can write the next line of code to explore it a little more.
We can use Shift Return to keep our hands on the keyboard and our brains in the zone.
And finally, by adding a dynamic live view to a playground, we can create a second view of our model and we can seamlessly shift between manipulating it in a graphical environment and using code.
So whether you're a beginner, just learning about new Apple APIs or an experienced programmer trying to sketch out the bones of their next great app, the next time you have a coding inspiration we invite you to get started with a playground.
Just in case you're still looking for ideas I've got three right here.
Number one if you're creating your own API, one of the best ways to showcase it is to create a follow along tutorial for your API.
Users can execute the code step-by-step and see in real time what it does.
Number two you can download and explore some publicly available data using the playground step-by-step to drill down into your data.
You could get this from maps, from local government, or perhaps a class project.
Finally, like I did, you could create a game or an animation.
Start off simple using SpriteKit or SyncKit and line by line enhance it until it's completely awesome.
So I hope we've shown you today that playgrounds are not a toy.
They're fun but they're serious fun.
They allow you to explore code and data interactively.
This is great whether you've downloaded an unknown snippet of JSON using a rest API from the Internet, or if you're dealing with hundreds of thousands or millions of lines of data for a machine learning application.
And to find out more about that use case I encourage you to download and watch the Create ML sessions in your WWDC application.
Secondly there's really no better way to learn how to use Apple APIs.
Whether you're just getting started or your trying out a new API, which you've learned about at this WWDC.
You don't just have to use Apple's APIs.
You can also import your own frameworks into playgrounds.
And one of the best ways to showcase this is to create custom representations of your data types allowing developers to view the most relevant information at a glance.
And to talk more about these two advanced concepts, I'd like to invite TJ to the stage.
Thank you, Alex.
My name is TJ Usiyan and I'm an Xcode Engineer.
By the time I finish my section, I'm sure that all of you will agree that every librarian framework that you ship will and can be improved with the addition of a playground.
Playgrounds provide a richer experience when providing readme's, tutorials, and general API documentation.
One of the ways that they can do this is by, as Alex said, providing your own representation in playgrounds.
I'm going to cover all of these things starting with Custom Playground Display Convertible, which will allow you to provide custom representations of your types in playgrounds so that users can get a nice summary.
I'll follow that up with how to import your frameworks into playgrounds.
And finally, I'll cover a little bit of troubleshooting tips for when things don't go exactly as you'd expect.
Let's start with Playground Display Convertible.
So as you know, when a user types in a line of code values show up on the right hand side in the result sidebar.
For types that are no optimized for playgrounds there are two ways that playgrounds will generate this description.
For types that do not conform to Custom String Convertible, we will create a structured representation using the Swift type.
For types that do conform to Custom String Convertible, we will use the result of calling descriptions.
When this isn't enough sometimes your users will tap on the Quick Look button on the right-hand side.
They will also tap or click on the Inline Results button.
When they do this a custom representation will show up.
Often a textual representation.
And for many types this is perfectly enough but sometimes maybe you would like to return a number.
This is still text though and there are times when text isn't going to be enough and you would like to return something graphical, maybe a picture.
The way to control what you return is to implement Custom Playground Display Convertible, a new protocol introduced in Xcode 9.
3 and Swift 4.
1.
It replaces Custom Playground Quick Lookable, which was deprecated in the same versions.
Let's take a look at conformance right now.
You can see here that conforming involves only returning one property, Playground Description.
Playground Description is of type Any, which means you can return anything that you feel best describes your value.
Now, there are certain types that have specialized representations already and those are provided by Apple.
Here's a list of the types with specialized representations as of Xcode 9.
3 and Swift 4.
1.
The types on the left have a particularly textual representation.
The types on the right have a graphical representation.
I invite you to try each of these and decide which best represents your value in a playground.
Once you've done this you'll want to ship all of your types, and your values, and your API to your users.
I'm going to show you how to import your own custom frameworks into playgrounds alongside Apple frameworks.
Typically, when you build a single framework in a project, that framework will end up in the Built Products Directory.
When you want to import it into a playground, that is where the playground will work.
The simplest way to make sure that your playground will see your framework is to add the playground to your project.
This is the strategy that I suggest for simple projects where you have access the project and are willing to edit it.
This is what that would look like in the Project Navigator.
Once you've added this project, or once you've added this playground to your project, I have a little bit of advice.
Remember building is very much like walking in that you have to remember to build before you run.
Now, sometimes you have more than one project, more than one framework, maybe you have two, three, four, and in this case that Built Products Directory situation that I just described is actually multiplied.
There are multiple Build Product Directories if you have separate projects.
This can be a problem when you want to import your code into a playground.
The simplest way to address this is to add each project to a workspace, a single workspace, and then when you build each project, those frameworks will end up in that one Built Products Directory for your workspace.
After that just add the playground to that workspace and everything should be fine.
This is what that should look like in the project navigator.
Now, let's say you've done this, you followed my instructions and things don't work out how you expect.
You say, "TJ lied to me.
" You're going to want to check the Built Products Directory to make sure that everything ends up there as you expect.
Here's how you can do that.
You're going to go to File, Project Settings, and then we're going to click the Advanced button.
On this screen in light gray we'll see that there is a Products destination.
You'll click on that and that should bring you directly to the Built Products Director for the project that you have open.
This is what that should look like in Finder.
Now let's see all of this brought together in a demo.
Now those of you who know me know that I have a pretty enduring interest in music.
I'm actually so interested in music that I have found this new notation, well new to me notation, called Helmholtz notation.
And I feel that many, many people should know about this and it should be much more widely used.
So I've created a framework to share with other developers so that they can use it in their code.
You can see here that I've included a playground and I've also, as the result of extensive research on Wikipedia written up a little playground that describes the notation.
Follow it, followed by a few values so that we can see the results on the right hand side with the notation.
If I render this documentation this will all end up in Pros with the links highlighted in blue just as Tibet spoke of.
And before I build, or before I run I'm going to build.
Then let's run our playground, yay.
You can see here that on the right-hand side in the results I have this interesting notation.
I really think that this notation is interesting because the lower pitches are represented by uppercase letters.
The higher pitches are represented by lowercase letters and the exact octave is indicated by either commas or apostrophes, the count thereof.
Now, hopefully you all get this looking at this notation, and hopefully I've explained it very well, but I've actually had some trouble with some of the people I'm tutoring.
They're not taking to it as well as I'd like.
So I actually have a separate framework that I've created with a keyboard visualization that I think will really help them ease into this notation.
Since I want to use that, I'm actually going to create a separate playground in a workspace where I can import both frameworks without changing either of the frameworks.
So to do that I'm going to quickly close this, I'm going to create a brand new workspace by going to File, New Work Space, and I'm going to name this Tutoring.
Just put that on the desktop.
Then I'm going to add each framework by going to File, Add Files.
I'm going to start with Helmholtz, my framework that I just had open, then File, right there, Keyboard.
Then I'm going to add a new playground by going to File, New, Playground.
A blank playground is fine.
My Playground is a fine name, a fine as name as any.
I'm going to start by importing Helmholtz, and My Keyboard.
After that I'm just going to quickly do a little test to make sure that pitches show up as I expect.
I'm going to build each of my frameworks.
I'm going to make sure to choose each one from the schemes.
Later on I might want to make a separate scheme that builds both of these projects in one go, but I don't have time on stage right now.
And then I'm going to run My Playground in it.
Everything works as expected.
But again this visualization is not helping.
I have some younger students who have only seen a piano, so I have a little snippet here that quickly creates a view in playground description, configures it, and actually I have one more line that I wanted to write on stage.
Custom text equals description.
And after I configure my view I'm going to return it.
Simple as that.
Made much simpler by the fact that I happen to have a framework already on hand.
Now, I want to run this line, line 4 again, but with my conformant.
So I'm going to reset this playground by clicking on the stop button down here.
And then I'm going to rerun this entire playground after I add my inline result.
And you can see here --  You can see here that I have a nice visualization of a keyboard that my students can recognize along with the notation that I'm trying to teach.
Now let's cover or let's go back over what we've learned today.
Tibet covered the fundamentals of playgrounds, the layout and playground markup syntax.
Alex explained the power of running step-by-step in playgrounds.
And I covered Custom Playground Display Convertible and importing your own code.
So hopefully, now that I've given this session and all of us have -- and we've explained playgrounds and the power that you can get, we hope to see that every project has a playground next year.
If you have any questions please feel free to visit us in the labs and we'll see you next year.

Now, here’s the code to assign the Live View property of the Playground Page to a UIView object. You can also assign either a class or a view controller.

You’d have to import the framework PlaygroundSupport for that, and UIKit as well.

let view = UIView(frame: CGRect(x: 0, y:0, width: 1024, height: 768)
PlaygroundPage.current.live = view 
In the navigation pane, you’ll see there’s two folders: Sources (for all the auxiliary code) and Resources (for all image and audio assets).

Playgrounds don’t have Storyboards. You can create a view (UIView) of any size (max 1024 x 768) programmatically.
PlaygroundSupport is a framework for doing things like accessing a playground page and managing its execution, managing live views, and sharing and accessing persistent data.

## Creating Rich Documentation with Markup
Swift Playgrounds lets you create beautiful documentation give your playgrounds an extra bit of polish (that is easier to read than the regular comments) using a language called Markup.
The basic syntax for Markup for rich documentation is as follows:
... 

It is especially great when you're making a playground to share with others.
With markup you can include stylized text, images, and video in your playground.
Now let's take a quick walkthrough what is possible with markup.
Here I've included some markup comments with text for a poem I'm writing.
A markup comment is like a regular comment but with a colon after the forward slashes.
The rest of the comment is then treated as markup text.
If you have multiple lines of comments next to each other they form one block of markup text.
You can also use multiline comments by putting a colon after the first asterisks.
Here's our markup in Xcode now.
It is showing the raw markup of the poem I wrote.
To show it in its rendered form, select the button in the top right corner of the window, which shows Xcode's Inspector.
Then select Render Documentation under Playground Settings.
The lines in my poem are now rendered.
Other interesting things you can do with the markup are adding headings to a Playground peach.
You can use headings to create structure in your playground.
You can use number signs to supply up to three levels of heading.
In this example the title of my poem "Roses are Red" as a first level heading, the subtitle, "An Ode to Markup" as a second level heading, and the byline as a third level heading.
Remember to add at least one space between the number sign and the heading string, otherwise you'll have a number sign connected to your heading when rendered.
This is what the headings look like rendered when included with the lines in my poem.
You can see that the first level heading is largest, followed by the second level, and then the third level heading.
You can also format the text in your markup content.
You can wrap a string of characters on a single asterisk on each side to italicize the text between the asterisks.
You can also use backticks to display text with Code Font.
Finally, if you use two asterisks instead of one the text will be bold.
Let's take a look at this rendered.
You can see that red and blue are italicized.
Markup is in Code Font and fun is in bold.
Let's take a look at using lists in markup.
If a markup comment starts with a number followed by a period, it will create an item in a numbered list.
In this example, I've added the lines of my poem to a numbered list.
Here you can see the lines of my poem rendered in a number list, each line representing an item in a numbered list.
You can also create a bullet to list in markup.
A bulleted list is like a number list except each line starts with an asterisks instead of a number.
This is how my poem in rendered in a bulleted list with each line in my poem represented as a bulleted item in a bulletin list.
Markup can also contain links.
In this example I've created a link to roses and violets.
To create a link you wrap the text in brackets and then place the destination of the link in parentheses after.
Another way you can create a link is by using a reference.
In this example I've created a reference named 1, but this can be any string.
It doesn't have to be a number.
When creating and using a link reference you wrap the name in brackets.
When creating a reference you add a colon and then the destination to the link.
Here are the links represented in rendered form, Roses, Violets, and Fun are shown in blue to represent a link.


### sources
[1]: https://developer.apple.com/library/content/documentation/Xcode/Reference/xcode_markup_formatting_ref/index.html
[From Hacking with Swift: "How to create live playgrounds in Xcode"](https://www.hackingwithswift.com/example-code/uikit/how-to-create-live-playgrounds-in-xcode)  
[Developing iOS 11 Apps with Swift by Stanford](https://itunes.apple.com/gb/course/developing-ios-11-apps-with-swift/id1309275316)  
[Using JSON with Custom Types](https://developer.apple.com/documentation/foundation/archives_and_serialization/using_json_with_custom_types)    
[Swift Playgrounds Author Template](https://developer.apple.com/download/more/?=Swift%20Playgrounds%20Author%20Template)    
[Swift Playgrounds - for iPad](https://developer.apple.com/documentation/swift_playgrounds)   
[Swift Standard Library](https://developer.apple.com/documentation/swift/swift_standard_library)    
[Authoring Rich Playgrounds](https://developer.apple.com/videos/play/wwdc2015/405/)  
[Introducing Swift Playgrounds](https://developer.apple.com/videos/play/wwdc2016/408/)    
[What’s New in Swift Playground](https://developer.apple.com/videos/play/wwdc2017/408/)  
[Ray Wenderlich video - Swift Playgrounds in Depth](https://www.raywenderlich.com/4345-swift-playgrounds-in-depth)    
[Making a Swift Playground in Xcode](https://www.youtube.com/watch?v=rL9A0LeGxFg&feature=youtu.be)    
[Rapid, Interactive Prototyping With Xcode Playgrounds](https://code.tutsplus.com/tutorials/rapid-interactive-prototyping-with-xcode-playgrounds--cms-26637)  
[Student Submissions for the WWDC 2017 Scholarship/](https://github.com/wwdc/2017/)    
[Student submissions for the WWDC 2018 Scholarship](https://github.com/wwdc/2018)  
[Awesome Swift Playgrounds](https://github.com/uraimo/Awesome-Swift-Playgrounds)  
[An Introduction to Swift Playgrounds](https://www.techotopia.com/index.php/An_Introduction_to_Swift_Playgrounds)  
[How to create live playgrounds in Xcode](https://www.hackingwithswift.com/example-code/uikit/how-to-create-live-playgrounds-in-xcode)
[FreeCodeCamp - How to make something with Swift Playgrounds](https://www.freecodecamp.org/news/how-to-make-something-with-swift-playgrounds-33e560b84184/)

Tibet Rooney-Rabdau,  Alex Brown and TJ Usiyan of Apple - [Getting the Most out of Playgrounds in Xcode - WWDC2018](https://developer.apple.com/videos/play/wwdc2018/402/)

