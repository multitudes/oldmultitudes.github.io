# best WWDC videos according to Paul Hudson

## Embracing Algorithms - Dave Abrahams 

meet crusty!
what is an Algorythm? 

algorithm | ˈalɡərɪð(ə)m |
noun
a process or set of rules to be followed in calculations or other problem-solving operations, especially by a computer: a basic algorithm for division.
check the standard library in swift
 
 loops are expensive

O(n) loop containing O(n) is O(n-squared)
O(nlogn) similar to O(n) because flattens out 

 removing shapes from an array of shapes. how to do this 
 
why is documentation important?
because we build on the blocks to higher abstractions and we need to understand how our code is based.

``` swift
extension Canvas {
mutating func deleteSelection() {
}
shapes.removeAll(where: { $0.isSelected })
}
```
“No Raw Loops” - Sean Parent (a.k.a. “Crusty's cousin”), C++ Seasoning
“If you want to improve the code quality in   your organization, replace all of your coding guidelines with one goal: 
 
No Raw Loops” •Sean Parent, C++ Seasoning
Sean Parent, C++ Seasoning https://channel9.msdn.com/Events/GoingNative/2013/Cpp-Seasoning
Alexander Stepanov and Paul McJones, Elements of Programming https://www.youtube.com/watch?v=Ih9gpJga4Vc
Swift Algorithms Prototype https://github.com/apple/swift/blob/master/test/Prototypes/Algorithms.swift
Swift Standard Library Documentation https://developer.apple.com/documentation/swift/swift_standard_library
https://developer.apple.com/wwdc18/223

Related Videos
https://developer.apple.com/videos/play/wwdc2018/406
https://developer.apple.com/videos/play/wwdc2018/229

## Prototyping: Fake It Till You Make It
Session 223 (wwdc14)
Jeffrey Traer Bernstein, Linda Dong, Julian Missig, Mark Hauenstein
Designers/Prototypers

https://developer.apple.com/videos/play/wwdc2014/223/
wish:
Idea -> App -> $$$
reality
Idea -> App -> 😢

better
Idea -> Prototype -> Prototype -> Prototype -> App

Two Reasons to Prototype Test ideas 
Save time and money building the right things 
Get new ideas  
Make the experience of your product better

Make fake apps
Show people
Learn from their feedback
Three Questions
Do you know how to __________? Is it easy to _________?
How can we make this better?
 
Who?
The people your app is for
 
Don’t
Argue, defend, dismiss

we use for this:
Pictures -> Keynote
Animation -> Keynote 
Interaction -> Core Animation

Designing Great Apps
http://developer.apple.com/design
Keynote Files and Toast Code
https://developer.apple.com/library/ios/toastmodern_sample

## Advanced Scrollviews and Touch Handling Techniques
Scrollviews build on gesture recognizers and underlying multi-touch mechanics to provide a fundamental piece of the iOS user experience. 

ops this one I skipped because too hard! Too much obj-c code that I dont know yet..

## Introducing the New System Fonts
This is incidentally one of the videos I watched at the time when Apple made them available online. Really beautiful and inspiring how much work goes into what we take for granted

Visual perception is largely about illusion

fonts make text possible
Calles as a grotesque, aniother word for sams serif
SF compact for watch

https://developer.apple.com/videos/play/wwdc2015/804

##  Inclusive App Design



https://developer.apple.com/videos/play/wwdc2016/801

Links:
[Human Interface Guidelines - iOS Design Themes](https://developer.apple.com/design/human-interface-guidelines/ios/overview/themes/)
[Contrast ratio by Lea Verou](https://contrast-ratio.com/)
[Colour Blindness](http://www.colourblindawareness.org/colour-blindness/)
[Accessibility for Developers](https://developer.apple.com/accessibility/)
[About Text Handling in iOS](https://developer.apple.com/library/archive/documentation/StringsTextFonts/Conceptual/TextAndWebiPhoneOS/Introduction/Introduction.html#//apple_ref/doc/uid/TP40009542)
[Web Content Accessibility Guidelines ](https://www.w3.org/TR/WCAG/#visual-audio-contrast)
[Human Interface Guidelines](https://developer.apple.com/design/human-interface-guidelines/watchos/overview/themes/)
[Internationalization Quick Tips for the Web](https://www.w3.org/International/quicktips/)
[Text Programming Guide for iOS](https://developer.apple.com/library/archive/documentation/StringsTextFonts/Conceptual/TextAndWebiPhoneOS/CustomTextProcessing/CustomTextProcessing.html#//apple_ref/doc/uid/TP40009542-CH4-SW65)
[UIFontDescriptor](https://developer.apple.com/documentation/uikit/uifontdescriptor#//apple_ref/doc/constant_group/Text_Styles)
[UIView](https://developer.apple.com/documentation/uikit/uiview#//apple_ref/occ/instp/UIView/readableContentGuide)
[Human Interface Guidelines - tvOS](https://developer.apple.com/design/human-interface-guidelines/tvos/overview/themes/)
[The World's Writing Systems](https://global.oup.com/academic/product/the-worlds-writing-systems-9780195079937?cc=us&lang=en&)
[The Elements of Typographic Style ](https://www.indiebound.org/book/9780881792119?aff=stewf)
[Fonts for Apple Platforms](https://developer.apple.com/fonts/)
[Human Interface Guidelines - macOS](https://developer.apple.com/design/human-interface-guidelines/macos/overview/themes/)
[Non-latin Typefaces](https://www.abebooks.com/9780950416151/Non-latin-Typefaces-Bride-Library-London-0950416150/plp)

Related Videos - WWDC 2016
[Auditing Your Apps for Accessibility](https://developer.apple.com/videos/play/wwdc2016/407)
[Designing Great Apple Watch Experiences](https://developer.apple.com/videos/play/wwdc2016/804)
[Disability and Innovation: The Universal Benefits of Accessible Design](https://developer.apple.com/videos/play/wwdc2016/104)
[Internationalization Best Practices](https://developer.apple.com/videos/play/wwdc2016/201)
[Iterative UI Design](https://developer.apple.com/videos/play/wwdc2016/805)
[Making Apps Adaptive, Part 2](https://developer.apple.com/videos/play/wwdc2016/233)
[Typography and Fonts](https://developer.apple.com/videos/play/wwdc2016/803)
[What's New in Accessibility](https://developer.apple.com/videos/play/wwdc2016/202)
[What's New in International User Interfaces](https://developer.apple.com/videos/play/wwdc2016/232)