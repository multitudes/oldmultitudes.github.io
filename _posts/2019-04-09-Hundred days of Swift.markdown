---
layout: post
title:  "100 Days Of Swift"
date:   2010-05-22
categories: iOS, developer
comments: true
published: true
---


<div class="message">
"iOS and macOS programs have long been written in a language called Objective-C. In the summer of 2014, Apple introduced a new and exciting language for writing apps called Swift" 
<br><cite></cite>
</div>

 
I have been recently very much enjoying the [100 days of Swift by Paul Hudson](https://www.hackingwithswift.com/100).  
The only thing I am missing is an index! When I am looking for old content I get stranded or need to google. There is no index on the website and after a certain number of projects under your belt you feel the need to revisit some of the staff. Where was that petition API again ? :)

This is the missing index for the 100 days of Swift! 

## Days 1 - 12 - Introduction to Swift   

All what you need to know about optionals and closures etc.  
See my other post with more details [here](https://multitudes.github.io/2019/04/Some-Swift-tips-for-beginner-and-intermediate.html).

<hr>

## Days 13 - 15 - Consolidation and review

<hr>

## Starting iOS

##  Project 1 : Storm Viewer

#### Day 16

> Dennis Ritchie, the inventor of the C programming language and co-inventor of UNIX, once said “the only way to learn a new programming language is by writing programs in it.”

- FileManager

```swift
let fm = FileManager.default
let path = Bundle.main.resourcePath!
let items = try! fm.contentsOfDirectory(atPath: path)
```
- app directories / bundles
-  `for item in items { if item.hasPrefix("nssl"){ // }}`
-  UITableViewController
- navigation controller -  Embed In -  Navigation Controller
- Methods to display cell

```swift
override func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
    return pictures.count
}
override func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        let cell = tableView.dequeueReusableCell(withIdentifier: "Picture", for: indexPath)
        cell.textLabel?.text = pictures[indexPath.row]
return cell
}
```
#### Day 17 

> as Walt Disney said, “of all our inventions for mass communication, pictures still speak the most universally understood language.”

- Auto Layout
- `@IBOutlet var imageView: UIImageView!`
- didSelectRowAt

```swift
override func tableView(_ tableView: UITableView, didSelectRowAt indexPath: IndexPath) {
    
    // 1: try loading the "Detail" view controller and typecasting it to be DetailViewController
    if let vc = storyboard?.instantiateViewController(withIdentifier: "Detail") as? DetailViewController {
    
    // 2: success! Set its selectedImage property
    vc.selectedImage = pictures[indexPath.row]

    // 3: now push it onto the navigation controller
    navigationController?.pushViewController(vc, animated: true)
    }
}
```

- property on UINavigationController called hidesBarsOnTap  

```swift
override func viewWillAppear(_ animated: Bool) {
    super.viewWillAppear(animated)
        navigationController?.hidesBarsOnTap = true
}

override func viewWillDisappear(_ animated: Bool) {
    super.viewWillDisappear(animated)
        navigationController?.hidesBarsOnTap = false
}
```

- `title = "Storm Viewer"`
- `navigationController?.navigationBar.prefersLargeTitles = true`
- `navigationItem.largeTitleDisplayMode = .never`

#### Day 18

- Wrap up

<hr> 

##  Project 2 - Guess The Flag
#### Day 19
> Saint Augustine said “the world is a book, and those who do not travel read only a page.”

- pixels and points - retina screens - file@2x.png  file@3x.png
- `button1.setImage(UIImage(named: countries[1]), for: .normal) `
- UIButton and CALayer - CGColor:  `button1.layer.borderColor = UIColor.lightGray.cgColor`

#### Day 20

> Steve Jobs said, "I believe life is an intelligent thing: that things aren't random.” 

- shuffled() to return a new, shuffled array. shuffle() for in-place shuffling
- Int.random(in: 0...2)
- @IBAction func buttonTapped(_ sender: UIButton) {}
- Tag - `sender.tag`
- UIAlertController()

```swift
let ac = UIAlertController(title: title, message: "...", preferredStyle: .alert)
ac.addAction(UIAlertAction(title: "Continue", style: .default, handler: askQuestion))
present(ac, animated: true)

...
func askQuestion(action: UIAlertAction!) {
...
}
```
#### Day 21 - Wrap up

>John Carmack once said, “focused, hard work is the real key to success. Keep your eyes on the goal, and just keep taking the next step towards completing it. If you aren't sure which way to do something, do it both ways and see which works better.”

<hr>

##  Project 3 - Social media
#### Day 22
>The famous Brazilian author Paulo Coelho said, “Twitter is my bar: I sit at the counter and listen to the conversations, starting others, feeling the atmosphere.”

- UIActivityViewController  - share by iMessage, by email and by Twitter and Facebook, as well as saving the image to the photo library, assigning it to contact, printing it out via AirPrint, and more

```swift
navigationItem.rightBarButtonItem = UIBarButtonItem(barButtonSystemItem: .action, target: self, action: #selector(shareTapped))

@objc func shareTapped() {
    guard let image = imageView.image?.jpegData(compressionQuality: 0.8) else {
    print("No image found")
    return
}
let vc = UIActivityViewController(activityItems: [image], applicationActivities: [])
vc.popoverPresentationController?.barButtonItem = navigationItem.rightBarButtonItem
present(vc, animated: true)
```
<hr>

## Day 23: Consolidation II

<hr>

## Web views, user input, and Auto Layout

##  Project 4 - Easy browser
#### Day 24 
> Alexis Ohanian, the founder of Reddit, once said “to join in the industrial revolution, you needed to open a factory; in the Internet revolution, you need to open a laptop.”

-   WKWebView // import WebKit
- First delegate pattern | Delegation is what's called a programming pattern – a way of writing code
``` swift
override func loadView() {
    webView = WKWebView()
    webView.navigationDelegate = self
    view = webView
}
```
- In our code, we're setting the web view's navigationDelegate property to self, which means "when any web page navigation happens, please tell me – the current view controller.” You must conform to the protocol, In the case of navigationDelegate, all these methods are optional.
- class ViewController: UIViewController, WKNavigationDelegate { ..
``` swift
let url = URL(string: "https://www.hackingwithswift.com")!
webView.load(URLRequest(url: url))
webView.allowsBackForwardNavigationGestures = true
```
- https:// for your websites - > App Transport Security
- delegate function `func webView(_ webView: WKWebView, didFinish navigation: WKNavigation!) {title = webView.title}`

#### Day 25

> If there’s one Martin Fowler quote that I love, it’s this: “I'm not a great programmer; I'm just a good programmer with great habits.” 

- Monitoring page loads: UIToolbar - holds and shows a collection of UIBarButtonItem objects 
- UIProgressView
- key-value observing, or KVO to monitor the loading of the sites
- `webView.addObserver` property
- using KVO, you must implement a method called observeValue()
- Refactoring
- contains() String method to see whether each safe website exists somewhere in the host name.

#### Day 26  - Wrap up


> There’s a Korean singer called Kwon Ji-yong – better known by the awesome stage name G-Dragon – who said, “you have to believe in yourself, challenge yourself, and push yourself until the very end; that's the only way you'll succeed

<hr>

##  Project 5 - Word Scramble
#### Day 27

> the US general George Patton once said, “accept the challenges so that you can feel the exhilaration of victory” –

- Capture lists in Swift: what’s the difference between weak, strong, and unowned references?
- Strong capturing
- Weak capturing
- Unowned capturing
- Strong reference cycles

- start.txt file
- `Bundle.main.url(forResource: "start", withExtension: "txt"){}`
- `allWords = startWords.components(separatedBy: "\n")`
- the `randomElement()` method of Swift’s arrays to choose one random item from all the strings.
- The `addTextField()` method just adds an editable text input field to the UIAlertController 

#### Day 28

> Blackadder: “Oh, I'm sorry, sir. I'm anaspeptic, phrasmotic, even compunctuous to have caused you such pericombobulation.”

- Swift uses a system of storing its characters, known as extended grapheme clusters - As a result, Swift doesn’t let us use str[7] to read the 8th character ..
- UITextChecker to check whether a string is spelled correcty
- UIKit was written in Objective-C before Swift’s strings came along, and it uses a different character system called UTF-16 – short for 16-bit Unicode Transformation Format – where the accent and the letter are stored separately.
- Emoji are measured differently with Swift strings and UTF-16 strings: Swift strings count them as 1-letter strings, but UTF-16 considers them to be 2-letter strings

#### Day 29 
- Wrap up

<hr>

##  Project 6 - Auto Layout in code
#### Day 30

> Coco Chanel once said that “fashion is architecture: it is a matter of proportions.” 

- Auto Layout in code: addConstraints with Visual Format Language

#### Day 31

> One of the three laws laid down by British science fiction writer Arthur C. Clarke is particularly well known: “any sufficiently advanced technology is indistinguishable from magic.”

- advanced Visual Formatting Language and Auto Layout anchors
- Every UIView has a set of anchors that define its layouts rules. The most important ones are widthAnchor, heightAnchor, topAnchor, bottomAnchor, leftAnchor, rightAnchor, leadingAnchor, trailingAnchor, centerXAnchor, and centerYAnchor.
- The “safe area” is the space that’s actually visible inside the insets of the iPhone X and other such devices – with their rounded corners, notch and similar. It’s a space that excludes those areas, so labels no longer run underneath the notch or rounded corners.

<hr>

##  Day 32 - Consolidation III

> Chris Bosh, an NBA All-Star basketball player, said “every athlete knows that you get good by practicing, by repeating the same moves until you achieve your goal” 

## Codable, buttons, and GCD
## Project 7 - Whitehouse petitions
#### Day 33

> Computing pioneer Mitch Kapor once said that “getting information off the internet is like taking a drink from a fire hydrant.”

- UITabBarController
- JSON – short for JavaScript Object Notation
- `Codable`
- custom struct called Petition , Petition.swift
- one of the advantages of structs in Swift is that it gives us a memberwise initializer

```swift
struct Petition: Codable {
var title: String
var body: String
var signatureCount: Int
}
```
- To decode JSON we need a second struct. This one will have a single property called results that will be an array of our Petition struct. This matches exactly how the JSON looks: the main JSON contains the results array, and each item in that array is a Petition.
- `if let data = try? Data(contentsOf: url) { ... }`

``` swift
override func viewDidLoad() {
    super.viewDidLoad()

    // let urlString = "https://api.whitehouse.gov/v1/petitions.json?limit=100"
    let urlString = "https://www.hackingwithswift.com/samples/petitions-1.json"

    if let url = URL(string: urlString) {
        if let data = try? Data(contentsOf: url) {
            // we're OK to parse!
            parse(json: data)
            }
        }
}

func parse(json: Data) {
    let decoder = JSONDecoder()

    if let jsonPetitions = try? decoder.decode(Petitions.self, from: json) {
        petitions = jsonPetitions.results
        tableView.reloadData()
}
}
```

#### Day 34

- injecting html code in detail view with  `webView.loadHTMLString(html, baseURL: nil)`
- Adding a second tapBarController in code

#### Day 35 
> Michelle Obama once said “through my education, I didn't just develop skills, I didn't just develop the ability to learn, but I developed confidence.”

- wrap up

## Project 8 - Build the layout in code - Swifty Words 
#### Day 36 
> Linus Torvalds, the creator of the massively popular Linux operating system, once said “talk is cheap; show me the code.” 

- UILabel for showing text
- UITextField to get text input
- UIButton
- Our ViewController haas a view property: view = UIView() is the parent class of all of UIKit’s view types: labels, buttons, progress views, and more
- label’s textAlignment property ex `scoreLabel.textAlignment = .right`

```swift
scoreLabel = UILabel()
scoreLabel.translatesAutoresizingMaskIntoConstraints = false
scoreLabel.textAlignment = .right
scoreLabel.text = "Score: 0"
view.addSubview(scoreLabel)
```
- NSLayoutConstraint.activate() method, which accepts an array of constraints
- `safeAreaLayoutGuide`  is the space available once you subtract any rounded corners or notches, inside that is the `layoutMarginsGuide`, which adds some extra margin so that views don’t run to the left and right edges of the screen

```swift
NSLayoutConstraint.activate([
    scoreLabel.topAnchor.constraint(equalTo: view.layoutMarginsGuide.topAnchor),
    scoreLabel.trailingAnchor.constraint(equalTo: view.layoutMarginsGuide.trailingAnchor),
    ...
    cluesLabel.numberOfLines = 0,
    cluesLabel.topAnchor.constraint(equalTo: scoreLabel.bottomAnchor)
    // more constraints to be added here!
])
```

- `numberOfLines` is an integer that sets how many lines the text can wrap over, but we’re going to set it to 0 – a magic value that means “as many lines as it takes.”
- Using `UIFont.systemFont(ofSize: 24)` will give us a 24-point font
- The `placeholder` property of text fields
- setting `isUserInteractionEnabled` to false
- use `setTitle()` to adjust the title on the button like `clear.setTitle("CLEAR", for: .normal)`


#### Day 37
- new string method to learn, called `replacingOccurrences()`
- Find a text file in the appbundle:
```swift
if let levelFileURL = Bundle.main.url(forResource: "level\(level)", withExtension: "txt") {
        if let levelContents = try? String(contentsOf: levelFileURL) {
            var lines = levelContents.components(separatedBy: "\n")
            lines.shuffle()
            for (index, line) in lines.enumerated() {
                let parts = line.components(separatedBy: ": ")
                let answer = parts[0]
                let clue = parts[1]
                ...

```
- a property observer
``` swift
var score = 0 {
    didSet {
        scoreLabel.text = "Score: \(score)"
    }
}
```
#### Day 38
> There are many well-known quotes from Shakespeare, but there’s one I think is particularly apt today: “the fool doth think he is wise, but the wise man knows himself to be a fool.”  


>In my talk at NSSpain 2018 I said “Auto Layout makes hard things easy, and easy things hard”   

## Project 9 - Grand Central Dispatch
#### Day 39
> Joss Whedon, the creator of Firefly, once said that “the secret to multitasking is that it isn't actually multitasking – it’s just extreme focus and organization.” (If you weren’t aware, Firefly played a big part in the development of Swift – the internal code name (“Shiny”) was from there  

- GCD allows to fetch the data without locking up the user interface
- Data's `contentsOf()` to download data from the internet, which is what's known as a blocking call. That is, it blocks execution of any further code in the method until it has connected to the server and fully downloaded all the data.
- code execution processes are called threads
- by default your own code executes on only one CPU, because you haven't created threads for other CPUs to work on.
- All user interface work must occur on the main thread, 
- if you’re accessing any remote resource, you should be doing it on a background thread
- three new `GCD functions`, but the most important one is called `async()`
- GCD creates for you a number of queues, and places tasks in those queues depending on how important you say they are.
- but more than one code block can be executed at the same time so the finish order isn't guaranteed.

“How important” some code is depends on something called “quality of service”, or QoS, which decides what level of service this code should be given
- 4 queues. queues affect the way the system prioritizes your work: User Interactive and User Initiated tasks will be executed as quickly as possible, Utility tasks will be executed with a view to keeping power efficiency as high as possible
- User Interactive: this is the highest priority background thread
- User Initiated
- The Utility queue: this should be used for long-running tasks that the user is aware of, but not necessarily desperate for now.
- The Background queue: this is for long-running tasks that the user isn't actively aware of, or at least doesn't care
- the default queue. This is prioritized between user-initiated and utility, and is a good general-purpose choice while you’re learning

- `DispatchQueue.global().async { [weak self] in`
- or 

``` swift

DispatchQueue.global(qos: .userInitiated).async { [weak self in
    if let url = URL(string: urlString) {
        if let data = try? Data(contentsOf: url) {
            self?.parse(json: data)
            return
        }
    }
    // this will go on the main thread too because UI work!!
        showError()
    
    }
}


// in the parse code.. the UI work goes back to main thread
DispatchQueue.main.async { [weak self] in
                self?.tableView.reloadData()
            }

```

- It's OK to parse the JSON on a background thread, but it's never OK to do user interface work there.
- another way of using GCD. `performSelector(inBackground:)` and `performSelector(onMainThread:)`

``` swift
performSelector(inBackground: #selector(fetchJSON), with: nil)

performSelector(onMainThread: #selector(showError), with: nil, waitUntilDone: false)

```
- Note: because performSelector() uses #selector, we need to mark our methods with the @objc attribute.

#### Day 40
> An old joke: " A programmer has a problem and thinks, “I can fix this using multitasking!” 
have Now problems! two they  

- race conditions are a whole category of bugs caused by one task completing before it was supposed to 
- GCD automatically handles thread creation and management, automatically balances based on available system resources, and automatically factors in Quality of Service 

## Consolidation IV
#### Day 41
> Ricky Mondello – one of the team who builds Safari at Apple – once said, “one of my favorite things about software engineering, or any kind of growth really, is coming back to something that you previously thought was too hard and knowing that you can do it.”  

- three Swift features that are so important
``` swift
for (index, line) in lines.enumerated() {
    let parts = line.components(separatedBy: ": ")
// ..
var score: Int = 0 {
    didSet {
        scoreLabel.text = "Score: \(score)"
    }
}
// ..
DispatchQueue.global().async { [weak self] in
    // do background work

    DispatchQueue.main.async {
        // do main thread work
    }
}   
```
#### Day 42
> my favorite quote from Douglas Adams: “I may not have gone where I intended to go, but I think I have ended up where I intended to be.”  


#### Day 43
#### Day 44
#### Day 45
#### Day 46
#### Day 47
#### Day 48
#### Day 49
#### Day 50

#### Day 51
#### Day 52
#### Day 53
#### Day 54
#### Day 55

#### Day 56
#### Day 57
#### Day 58
#### Day 59
#### Day 60
#### Day 61
#### Day 62
#### Day 63
#### Day 64
#### Day 65
#### Day 66
#### Day 67
#### Day 68
#### Day 69
#### Day 70
#### Day 71
#### Day 72
#### Day 73
#### Day 74
#### Day 75
#### Day 76
#### Day 77
#### Day 78
#### Day 79
#### Day 80
#### Day 81
#### Day 82
#### Day 83
#### Day 84
#### Day 85
#### Day 86
#### Day 87

## Project 27 - custom drawing  
#### Day 88
> As Michelangelo once said, “every block of stone has a statue inside it and it is the task of the sculptor to discover it.”

- `Core Graphics` responsible for device-independent 2D drawing – when you want to draw shapes, paths, shadows, colors..
- let Interface Builder do the work : Editor > Resolve Auto Layout Issues > Reset to Suggested Constraints.
- Core Graphics sits at a lower technical level than UIKit. This means it doesn't understand classes you know like UIColor and UIBezierPath, so you either need to use their counterparts (CGColor and CGPath respectively)
- Core Graphics differentiates between creating a path and drawing a path.

- Core Graphics is extremely fast and can work on a background thread – something that UIKit can't do 
- `UIGraphicsImageRenderer` class. This was introduced in iOS 10 to allow fast and easy graphics rendering. It isn’t a Core Graphics class; it’s a UIKit class, but it acts as a gateway to and from Core Graphics for UIKit-based apps.
- In Core Graphics, a context is a canvas upon which we can draw, but it also stores information about how we want to draw 
- When you create a renderer, you get to specify how big it should be. To kick off rendering you can either call the image() function to get back a UIImage of the results, or call the pngData() and jpegData() methods to get back a Data object in PNG or JPEG format 
- the renderer image() method accepts a closure as its only parameter, which is code that should do all the drawing. It gets passed a single parameter which is a reference to a UIGraphicsImageRendererContext to draw to.
- the `cgContext` property gives us the full power of Core Graphics.
- five new methods: `setFillColor()` `setStrokeColor()` `setLineWidth()` `addRect()` `drawPath()` which are called on the Core Graphics context that comes from ctx.cgContext
- drawing circles (or indeed any elliptical shape) in Core Graphics is done by specifying its rectangular bounds.
- create a checkerboard - check `CICheckerboardGenerator`
- drawImagesAndText()
- put an attributed string into a graphic? attributed strings have a built-in method called draw(with:)


#### Day 89
> Carl Sagan once said, "if you wish to make an apple pie from scratch, you must first invent the universe."

> Swift was first introduced way back in 2014, at Apple’s annual Worldwide Developer Conference (WWDC). When showing off the new language, Chris Lattner (the creator of Swift) took to the stage and immediately did something that was revolutionary for us – at least back then: he created a Swift playground in Xcode.

- Wrap up and challenges

## MILESTONE: PROJECTS 25-27

#### Day 90
> "As John Quincy Adams once said, “patience and perseverance have a magical effect before which difficulties disappear and obstacles vanish.”

- `#targetEnvironment`(simulator) compiler directive. Swift has several of these, like `#line` and `#if swift`. 
- `#line` is easy enough: when your code gets built it automatically gets replaced with the current line number. You can also use #filename and #function, and the combination of these are very useful in debugging strings.
- The #if swift directive allows you to conditionally compile code depending on the Swift compiler version being used. So, you could write Swift 4.2 code and Swift 5.0 code in the same file, and have Xcode choose the right version automatically.

#### Day 91 - CORE GRAPHICS REDUX
> Fred Donaldson : “Children learn as they play. Most importantly, in play children learn how to learn.” 

> George Bernard Shaw said, “we don’t stop playing because we grow old; we grow old because we stop playing.” 

- Playground links for [ipad](https://www.hackingwithswift.com/playgrounds) and [xcode](http://hackingwithswift.com/files/playgrounds/Learn-Core-Graphics-Xcode.zip)

## PROJECT 28 - Use the iOS keychain - Secret Swift
#### Day 92
> Bruce Schneier – a well-known US cryptographer, security analyst, and writer, once said “if you think technology can solve your security problems, then you don't understand the problems and you don't understand the technology.”

- Touch ID, Face ID and the keychain. The first two are used to identify users biometrically using the fingerprint sensor on iPhones and iPads, or the face scanner on iPhone X or similar; the latter is a secure, encrypted data storage area on every device that you can read and write to.
- UserDefaults is great for its simplicity but isn't good for private data
- `NotificationCenter.default` to tell us when the keyboard changes or when it hides
- `adjustKeyboard()` method  
- a helpful class called `KeychainWrapper` . This class was not made by Apple; instead, it's open source software released under the MIT license, which means we can use it in our own projects as long as the copyright message remains intact.
- launch a function when leaving the app..   

```swift
let notificationCenter = NotificationCenter.default
notificationCenter.addObserver(self, selector: #selector(saveSecretMessage), name: UIApplication.willResignActiveNotification, object: nil)

// use the two functions
KeychainWrapper.standard.set(secret.text, forKey: "SecretMessage")
// and
secret.text = KeychainWrapper.standard.string(forKey: "SecretMessage") ?? ""
```
- Touch ID and Face ID are part of the Local Authentication framework, and our code needs to do three things Check whether the device is capable of supporting biometric authentication – that the hardware is available and is configured by the user.
- biometry system begin a check now. For Touch ID the string is written in code; for Face ID the string is written into our Info.plist file
- when we're told whether Touch ID/Face ID was successful or not, it might not be on the main thread. This means we need to use async() 
- `import LocalAuthentication`

#### Day 93

> As Gene Spafford once said, “the online truly secure system is one that is powered off, cast in a block of concrete and sealed in a lead-lined room with armed guards.”

- security, encryption in ios 
- If you use biometric authentication but store your data in UserDefaults, it can be read out by bypassing the app. If you store your data in the iOS keychain but don’t put it behind biometric authentication or similar, anyone can launch the app and just take it.

## PROJECT 29 - Exploding Monkeys
#### Day 94 
> 'Don’t practice until you get it right; practice until you can’t get it wrong.'

- `SKSpriteNode` subclass for buildings that sets up physics, draws the building graphic, and ultimately handles the building being hit 
- `import SpriteKit`
- three methods: `setup()` will set its name, texture, and physics. `configurePhysics()` will set up per-pixel physics for the sprite's `current texture`(texture will change as the game progresses. `drawBuilding()` will do the Core Graphics rendering of a building, and return it as a UIImage.
- define some collision bitmasks
- a new way to create colors: hue, saturation and brightness, or HSB. The helpful thing about HSB is that if you keep the saturation and brightness constant, changing the hue value will cycle through all possible colors – it's an easy way to generate matching pastel colors
- basic Swift feature `stride()`, which lets you loop from one number to another with a specific interval. 

```swift
for row in stride(from: 10, to: Int(size.height - 10), by: 40) {
```
- `Bool.random()` to generate either true or false randomly
- mixing UIKit and SpriteKit, our game view controller needs to house and manage the user interface, and the game scene needs to manage everything inside the game. But they also need to talk to each other:  


```swift
// Add this property to the game scene:
weak var viewController: GameViewController!
//Now add this property to the game view controller:
var currentGame: GameScene!

currentGame = scene as? GameScene   
currentGame.viewController = self
```


#### Day 95
> As Ernest Rutherford once said, “all of physics is either impossible or trivial: it is impossible until you understand it, and then it becomes trivial.”  

- create a player  

```swift
var player1: SKSpriteNode!

player1 = SKSpriteNode(imageNamed: "player")
        player1.name = "player1"
        player1.physicsBody = SKPhysicsBody(circleOfRadius: player1.size.width / 2)
        player1.physicsBody?.categoryBitMask = CollisionTypes.player.rawValue
        player1.physicsBody?.collisionBitMask = CollisionTypes.banana.rawValue
        player1.physicsBody?.contactTestBitMask = CollisionTypes.banana.rawValue
        
        // this tells not to be influenced by gravity
        player1.physicsBody?.isDynamic = false
        // put he player on top of the second building
        let player1Building = buildings[1]
        player1.position = CGPoint(x: player1Building.position.x, y: player1Building.position.y + ((player1Building.size.height + player1.size.height) / 2))
        addChild(player1)        
```

- A texture atlas is a set of pictures that are combined into a single image. to render one of those pictures SpriteKit loads the whole atlas and just draws the small window that represents the image you want.Texture atlases allows SpriteKit to draw lots of images without having to load and unload textures – it effectively just crops the big image as needed. Xcode automatically generates these atlases for us.open Assets.xcassets, right-click in the big empty space below AppIcon, and choose New Sprite Atlas
- converting degrees to radians is done with a fixed formula that we will put into a method called deg2rad():

```swift
func deg2rad(degrees: Int) -> Double {
    return Double(degrees) * Double.pi / 180
}
```

- SpriteKit uses a number of optimizations to help its physics simulation work at high speed. These optimizations don't work well with small, fast-moving objects, and our banana is just such a thing. To be sure everything works as intended, we're going to enable the usesPreciseCollisionDetection property for the banana's physics body. This works slower, but it's fine for occasional use.
-if we calculate the cosine of our angle in radians it will tell us how much horizontal momentum to apply, and if we calculate the sine of our angle in radians it will tell us how much vertical momentum to apply.

- we use the applyImpulse() method of its physics body, which accepts a CGVector as its only parameter and gives it a physical push in that direction.
- add collision detection . Make your gamescene conform to `SKPhysicsContactDelegate`
and in didMove()

```swift
physicsWorld.contactDelegate = self
```

- If the banana hit a player, we're going to call a new method named destroy(player:). If the banana hit a building, we'll call a different new method named bananaHit(building:), but we'll also pass in the contact point
- SpriteKit has a super-stylish and built-in way of letting you transition between scenes. For example, this will cross-fade in a new scene over 2 seconds:

``` swift
// on the main thread after a selay
DispatchQueue.main.asyncAfter(deadline: .now() + 2) {
    let newGame = GameScene(size: self.size)
    let transition = SKTransition.crossFade(withDuration: 2)
    self.view?.presentScene(newGame, transition: transition)
    self.changePlayer()
        newGame.currentPlayer = self.currentPlayer

        let transition = SKTransition.doorway(withDuration: 1.5)
        self.view?.presentScene(newGame, transition: transition)
}
```

- explosions are easy

``` swift
if let explosion = SKEmitterNode(fileNamed: "hitBuilding") {
        explosion.position = contactPoint
        addChild(explosion)
    }
```

- `convert()`, which asks the game scene to convert the collision contact point into the coordinates relative to the building node. 
- Core Graphics has quite a few blend modes that might look similar, but we're going to use one called `.clear`, which means "delete whatever is there already." 
- the abs() function makes negative number positive


#### Day 96
> Craig Federighi, senior vice president of software engineer at Apple, once said “people sometimes have a view of programming that is something solitary and very technical, but programming is among the most creative, expressive, and social careers.”

- wrap up

## PROJECT 29 - Instruments
#### Day 97
> as Edsger Dijkstra once said, “if debugging is the process of removing software bugs, then programming must be the process of putting them in.”

- Instruments. It ships as part of Xcode, and is responsible for profiling your app. "Profiling" is the term used when we monitor performance, memory usage and other information of an app, with the aim of improving efficiency.
- Press Cmd+I to run your app using Instruments. This will build your ode in Release mode, which men fully optimized for maximum performance 
- select Time Profiler
- Under the Debug menu on your Mac you’ll see a few options. Two in particular are very useful: `Color Blended Layers` shows views that are opaque in green and translucent in red. If there are multiple transparent views inside each other, you'll see more and more red. `Color Offscreen-Rendered` shows views that require an extra drawing pass in yellow. Some special drawing work must be drawn individually off screen then drawn again onto the screen, which means a lot more work.
Broadly speaking, you want "Color Blended Layers" to show as little red as possible, and "Color Offscreen-Rendered Yellow" to show no yellow.

```swift
		tableView.rowHeight = 90
		tableView.separatorStyle = .none
```

- 2000x2000 pixel jpeg images might only take up 500KB on disk, but when they are uncompressed by iOS they’ll need around 45 MB of RAM!
- Instruments > `Allocations instrument`
- maoolc means memory allocate
- some objects are persistent (created and still exist while the program was still running) and some are transient (created and since destroyed). 

#### Day 98
> As Izey Victoria Odiase said, “don't aim for perfection – aim for 'better than yesterday’.”

- When you create a UIImage using UIImage(named:) iOS loads the image and puts it into an image cache for reuse later.
- we can skip the image cache by creating our images using the UIImage(contentsOfFile:) initializer instead. This isn't as friendly as UIImage(named:) because you need to specify the exact path to an image rather than just its filename in your app bundle
- UIImage's cache is intelligent: if it senses memory pressure, it automatically clears itself to make room for other stuff.
- `title = image.replacingOccurrences(of: "-Large.jpg", with: "")`

```swift
// the timer was using memory through strong reference 
animTimer = Timer.scheduledTimer(withTimeInterval: 5, repeats: true) { timer in
// function to cancel the timer
override func viewWillDisappear(_ animated: Bool) {
    super.viewWillDisappear(animated)
    animTimer.invalidate()
}
```

- Hold up your right hand and repeat after me: “I will never ship an app without running it through Instruments first.” 
		


## Milestone
#### Day 99
> as the Greek philosopher Epictetus once said, “the greater the difficulty the more glory in surmounting it” 

- A failable initializer is one that might return a valid created object, or it might fail and return nil. We’re going to use this so that we can return nil if the image name can’t be found in the app bundle. a new UIImage extension that creates a new, failable, convenience initializer called UIImage(uncached:).

```swift
extension UIImage {
    convenience init?(uncached name: String) {
        if let path = Bundle.main.path(forResource: name, ofType: nil) {
            self.init(contentsOfFile: path)
        } else {
            return nil
        }
    }
}
```

- How to flip a UIView with a 3D effect: `transition(with:)`  - see code below


<hr>
## FINAL EXAM 
#### Day 100!
> As Aisha Tyler said, “success is not the absence of failure; it's the persistence through failure.”


PROJECT 27
#### Sources:

[GitHub HackingWithSwift](https://github.com/twostraws/HackingWithSwift)
[Talk at NSSpain Spain](http://vimeo.com/291590798)
[HACKING WITH SWIFT ONLINE](https://www.hackingwithswift.com/read)
[How to flip a UIView with a 3D effect: transition(with:)](https://www.hackingwithswift.com/example-code/uikit/how-to-flip-a-uiview-with-a-3d-effect-transitionwith)