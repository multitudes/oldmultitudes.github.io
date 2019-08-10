---
layout: post
title:  "Everything about Swift playgrounds"
date:   2001-06-15
categories: iOS, developer
comments: true
published: true
---
# achtung.. still a draft :)
Now, here’s the code to assign the Live View property of the Playground Page to a UIView object. You can also assign either a class or a view controller.

You’d have to import the framework PlaygroundSupport for that, and UIKit as well.

let view = UIView(frame: CGRect(x: 0, y:0, width: 1024, height: 768)
PlaygroundPage.current.live = view 
In the navigation pane, you’ll see there’s two folders: Sources (for all the auxiliary code) and Resources (for all image and audio assets).

Playgrounds don’t have Storyboards. You can create a view (UIView) of any size (max 1024 x 768) programmatically.
PlaygroundSupport is a framework for doing things like accessing a playground page and managing its execution, managing live views, and sharing and accessing persistent data.

## Creating Rich Documentation with Markup
Swift Playgrounds lets you create beautiful documentation (that is easier to read than the regular comments) using a language called Markup.

The basic syntax for Markup for rich documentation is as follows:


### sources

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
