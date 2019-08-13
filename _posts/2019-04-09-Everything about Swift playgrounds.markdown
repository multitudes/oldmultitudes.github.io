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

Whether a beginner just getting started with Apple APIs, a seasoned engineer with a deadline, or a data scientist building machine learning models,  Xcode playgrounds are probably the fastest way to get started coding against Apple's APIs.
In Xcode 10, playgrounds are faster and more responsive than ever allowing you to execute your code in a step-by-step fashion.

A blue line over the line numbers mean these lines are ready to execute and when you click the Play button this means run all of the blue lines up to and including the one with the play button on it.

The results are visible on the right-hand side.
You can also see that the play button has now gone gray. This indicates that these lines of code are no longer ready to execute. You just executed them.  
There's a second reason that they play button might be gray.
This means you're hovering over some code, which is not a top-level line of code. This includes code inside function brackets and inside of fall loop.
If you wish to execute a fall loop you need to move your pointer to the closing brace where the play button will go blue then you'll be able to execute it.
There's also a great keyboard shortcut, `Shift Return`. 
This is just like pressing Return at the end of typing a line of code, but it also means execute this line, and it move the cursor to the next line ready to write some more code.
Blue code also has a second interpretation.
It means code that it's safe to edit without resetting your playground.
Why is this important? If you edit code above the blue line this is modifying code that you've already executed. So you'll have to resent your playground to take account of your changes. When you edit code above the blue line, the playground resets automatically.
Sometimes you'll need to reset your playground manually and you can do this using the stop button in the Debug bar at the bottom of the screen.
So why run in a step-by-step fashion? Why have we added this feature? Firstly, executing just one more line is fast.
It's way faster than restarting a playground and waiting for it to catch up with your thoughts.
Secondly, it allows you to respond to live data.
Write a line of code, execute it, see what the results are, and this should lead you naturally to the next line of code to write.
And thirdly rerunning a playground every time can give you different values every time.
This can happen, for instance, if you're accessing a network resource or you're generating random numbers.
By executing step-by-step your data model stays stable and easier to understand.

Demo the game of Tic-tac-toe.

By running step-by-step we can explore an idea a line at a time.

This enables us to have a conversation between code and data.

Every time we learn a new fact we can write the next line of code to explore it a little more.

We can use Shift Return to keep our hands on the keyboard and our brains in the zone.

And finally, by adding a dynamic live view to a playground, we can create a second view of our model and we can seamlessly shift between manipulating it in a graphical environment and using code.
So whether you're a beginner, just learning about new Apple APIs or an experienced programmer trying to sketch out the bones of their next great app, the next time you have a coding inspiration we invite you to get started with a playground.

If you're creating your own API, one of the best ways to showcase it is to create a follow along tutorial for your API.
Users can execute the code step-by-step and see in real time what it does.
You can download and explore some publicly available data using the playground step-by-step to drill down into your data.
You could get this from maps, from local government, or perhaps a class project.
Finally you could create a game or an animation.
Start off simple using SpriteKit or SceneKit and line by line enhance it until it's completely awesome.

## They're fun but they're serious fun.

They allow you to explore code and data interactively.

## Playground Display Convertible.

So as you know, when a user types in a line of code values show up on the right hand side in the result sidebar.
For types that are no optimized for playgrounds there are two ways that playgrounds will generate this description.
For types that do not conform to `CustomStringConvertible`, we will create a structured representation using the Swift type.
For types that do conform to `CustomStringConvertible`, we will use the result of calling `descriptions`.

This is still text though and there are times when text isn't going to be enough and you would like to return something graphical, maybe a picture.
The way to control what you return is to implement `CustomPlaygroundDisplayConvertible`, a new protocol introduced in Xcode 9.3

It replaces CustomPlaygroundQuickLookable, which was deprecated in the same versions.

### How to import your own custom frameworks into playgrounds alongside Apple frameworks.

Typically, when you build a single framework in a project, that framework will end up in the Built Products Directory.
When you want to import it into a playground, that is where the playground will work.
The simplest way to make sure that your playground will see your framework is to add the playground to your project.
This is the strategy that I suggest for simple projects where you have access the project and are willing to edit it.

# till here


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

