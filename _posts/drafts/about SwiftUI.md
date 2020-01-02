#  First contact with SwiftUI

WWDC19 contains more large announcements than any in years, Everything you know about UIKit is still useful, and will be for a good few years.
What has changed is how we make our apps.If you’re already proficient with UIKit you can pick up SwiftUI in less than a day. 

Declarative UI is best understood in comparison to imperative UI, which is what iOS developers were doing before iOS 13SwiftUI is a user interface toolkit that lets us design apps in a declarative way. Imperative UI causes all sorts of problems, most of which revolve around state, which is another fancy term meaning “values we store in our code”. 

But SwiftUI doesn’t stop there: it also acts as a cross-platform user interface layer that works across iOS, macOS, tvOS, and even watchOS. This means you can now learn one language and one layout framework, then deploy your code anywhere.
Interface Builder doesn’t know much about our Swift code, and our Swift code doesn’t know much about Interface Builder.
problems exist because IB and Swift are very separate things. This isn’t a huge surprise – not only does Interface Builder date from way before the original Mac OS X was a thing, but it’s also very much designed around the way Objective-C works.

We no longer have to worry about creating source control problems when committing user interface work, because code is much easier to read and manage than storyboard XML.

So, if you ignored SwiftUI for a year, two years, or perhaps even more, there would be no shortage of jobs for you. No one – not even Apple, I think! – expects the iOS community to migrate over to SwiftUI at any sort of rapid pace.

Where can SwiftUI be used?
SwiftUI runs on iOS 13, macOS 10.15, tvOS 13, and watchOS 6,

a framework for creating apps on multiple platforms.

Does SwiftUI replace UIKit?
No. Many parts of SwiftUI directly build on top of existing UIKit components, such as UITableView. Of course, many other parts don’t – they are new controls rendered by SwiftUI and not UIKit.

SwiftUI is screamingly fast –
many operations bypass Core Animation entirely and go straight to Metal for extra speed.

Can you mix views from SwiftUI and UIKit?
Yes! You can embed one inside the other and it works great.

NSAttributedString: Incompatible with SwiftUI; use Text instead.

SwiftUI started long before that as a project from inside the watchOS team – about four years before, from what various folks have said.
In order to make SwiftUI a reality folks from the UIKit team, the Swift team, the Xcode team, the developer publications team, and more, all had to come together in secret to work on our behalf, and even today you won’t find them taking credit for their incredible work

Dave Abrahams, Luca Bernardi, Kevin Cathey, Nate Cook, John Harper, Taylor Kelly, Kyle Macomber, Raj Ramamurthy, Matt Ricketson, Jacob Xiao

The basic Single View App template gives you the following:
1. AppDelegate.swift. This is responsible for monitoring external events, such as if another app tries to send you a file to open.
2. SceneDelegate.swift. This is responsible for managing the way your app is shown, such as letting multiple instances run at the same time or taking action when one moves to the background.
3. ContentView.swift. This is our initial piece of user interface. If this were a UIKit project, this would be the ViewController class that Xcode gave us.
4. Assets.xcassets. This is an asset catalog, which stores all the images and colors used in our project.
5. LaunchScreen.storyboard. This is the screen that gets shown while your app is loading.
6. Info.plist is a property list file, which in this instance is used to store system-wide settings
for our app – what name should be shown below its icon on the iOS home screen, for
example.
7. A group called Preview Content, which contains another asset catalog called Preview
Assets.


``` swift
import SwiftUI

struct ContentView: View {
    var body: some View {
        Text("Hello World")
    }
}

struct ContentView_Previews: PreviewProvider {
    static var previews: some View {
        ContentView()
    }
}
```

ContentView is a struct
we get to benefit from all the immutability and simplicity of values types for our user interface
ContentView conforms to the View protocol. Everything you want to show in SwiftUI needs to conform to View, and really that means only one thing: you need to have a property called body that returns some sort of View.
the return type of body is some View. The some keyword is new in Swift 5.1 and is part of a feature called opaque return types, and in this case what it means is literally “this will return some sort of View but SwiftUI doesn’t need to know (or care) what.”Returning some View means that the body property will return something that conforms to the View protocol. inside the body property there’s Text("Hello World"), which creates a label of the text “Hello World”.
Finally, below ContentView is a similar-but-different struct called ContentView_Previews. This doesn’t conform to the View protocol because it’s specifically there to show view previews inside Xcode as opposed to be on-screen in a real app. This is why you’ll see it inside #if DEBUG and #endif lines – this code is only built into the finished product when our app runs in a debug environment because it doesn’t make sense in a production app.

``` swift
Text("This is an extremely long string that will never fit even the widest of Phones")
    .lineLimit(nil) 
    .font(.largeTitle) 
    .multilineTextAlignment(.center)
    .foregroundColor(Color.red)
```
We now have two modifiers below our text view, and that’s OK – you can just stack them up, and they all take effect.

### How to format text inside text views
``` swift
struct ContentView: View {
static let taskDateFormat: DateFormatter = {
   let formatter = DateFormatter()
       formatter.dateStyle = .long
           return formatter
    }()
var dueDate = Date()
var body: some View {
   Text("Task due date: \(dueDate, formatter: Self.taskDateFormat)")
    }
}
```

### Use the Image view to render images inside your SwiftUI layouts.

``` swift
var body: some View { 
Image(systemName: "cloud.heavyrain.fill")

// Finally, you can create an image view from an existing UIImage. As this requires more code, you’ll need to use the return keyword explicitly:

var body: some View { Image("example-image")
}
guard let img = UIImage(named: "example-image") else { fatalError("Unable to load image")
}
return Image(uiImage: img))
}
```

To load icons from Apple’s San Francisco Symbol set, use the Image(systemName:) initializer, passing in the icon string to load, like this:
`Image(systemName: "cloud.heavyrain.fill")`
And it also means you can ask SwiftUI to scale up the image to match whatever Dynamic Type text style it accompanies, if any:
`.font(.largeTitle)`

SwiftUI’s Image view has the ability to be scaled in different ways, just like the content mode of a UIImageView.
``` swift
Image("Screenshot")
 .resizable()
     .aspectRatio(contentMode: .fill)
 ```
 
 ## How to render a gradient
 ``` swift
 Text("Hello World") .padding()
 .foregroundColor(.white)
     .background(LinearGradient(gradient: Gradient(colors: [.white, .red]), startPoint: .top, endPoint: .bottom))
```

## How to display solid shapes

For example, if you wanted a 200x200 red rectangle, you would use this:

``` swift
Rectangle()
.fill(Color.red)
.frame(width: 200, height: 200)
```

Similarly, if you wanted a 50x50 blue circle you would use this:
``` swift
Circle()
.fill(Color.blue) .frame(width: 50, height: 50)
````

``` swift
Text("Hacking with Swift") .font(.largeTitle) .background(Circle()
 .fill(Color.red)
 .frame(width: 200, height: 200))
 ```
 
 
