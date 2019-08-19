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

## [Day 1-15 - Introduction to Swift](https://www.hackingwithswift.com/100/1)   

All what you need to know about optionals and closures etc.  
See my other post with more details here: [Some Swift for beginner and intermediate](https://multitudes.github.io/2019/04/Some-Swift-tips-for-beginner-and-intermediate.html).  


<hr>

## Starting iOS

##  Project 1 : Storm Viewer

#### [Day 16](https://www.hackingwithswift.com/100/16) 

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
- Methods to display cells:

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
#### [Day 17](https://www.hackingwithswift.com/100/17)  

> as Walt Disney said, “of all our inventions for mass communication, pictures still speak the most universally understood language.”

- Auto Layout
- `@IBOutlet var imageView: UIImageView!`
- didSelectRowAt

```swift
override func tableView(_ tableView: UITableView, didSelectRowAt indexPath: IndexPath) {
    
    // 1: try loading the "Detail" view controller and typecasting it to be DetailViewController
    if let vc = storyboard?.instantiateViewController(withIdentifier: "Detail") 
    as? DetailViewController {
    
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

#### [Day 18](https://www.hackingwithswift.com/100/18) 
> Maya Angelou once said, “nothing will work unless you do.”

[Challenge](https://www.hackingwithswift.com/review/hws/project-1-storm-viewer)

<hr> 

##  Project 2 - Guess The Flag
#### [Day 19](https://www.hackingwithswift.com/100/19) 
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
#### [Day 21](https://www.hackingwithswift.com/100/21)  - Wrap up

>John Carmack once said, “focused, hard work is the real key to success. Keep your eyes on the goal, and just keep taking the next step towards completing it. If you aren't sure which way to do something, do it both ways and see which works better.”

<hr>

##  Project 3 - Social media

#### [Day 22](https://www.hackingwithswift.com/100/22) 
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

#### [Day 23](https://www.hackingwithswift.com/100/23) : Consolidation II

<hr>

## Web views, user input, and Auto Layout

##  Project 4 - Easy browser
#### [Day 24](https://www.hackingwithswift.com/100/24)  
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

#### [Day 25](https://www.hackingwithswift.com/100/25) 

> If there’s one Martin Fowler quote that I love, it’s this: “I'm not a great programmer; I'm just a good programmer with great habits.” 

- Monitoring page loads: UIToolbar - holds and shows a collection of UIBarButtonItem objects 
- UIProgressView
- key-value observing, or KVO to monitor the loading of the sites
- `webView.addObserver` property
- using KVO, you must implement a method called observeValue()
- Refactoring
- contains() String method to see whether each safe website exists somewhere in the host name.

#### [Day 26](https://www.hackingwithswift.com/100/26)   - Wrap up


> There’s a Korean singer called Kwon Ji-yong – better known by the awesome stage name G-Dragon – who said, “you have to believe in yourself, challenge yourself, and push yourself until the very end; that's the only way you'll succeed

<hr>

##  Project 5 - Word Scramble
#### [Day 27](https://www.hackingwithswift.com/100/27) 

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

#### [Day 28](https://www.hackingwithswift.com/100/28) 

> Blackadder: “Oh, I'm sorry, sir. I'm anaspeptic, phrasmotic, even compunctuous to have caused you such pericombobulation.”

- Swift uses a system of storing its characters, known as extended grapheme clusters - As a result, Swift doesn’t let us use str[7] to read the 8th character ..
- UITextChecker to check whether a string is spelled correcty
- UIKit was written in Objective-C before Swift’s strings came along, and it uses a different character system called UTF-16 – short for 16-bit Unicode Transformation Format – where the accent and the letter are stored separately.
- Emoji are measured differently with Swift strings and UTF-16 strings: Swift strings count them as 1-letter strings, but UTF-16 considers them to be 2-letter strings

#### [Day 29](https://www.hackingwithswift.com/100/29) 
- Wrap up

<hr>

##  Project 6 - Auto Layout in code
#### [Day 30](https://www.hackingwithswift.com/100/30)

> Coco Chanel once said that “fashion is architecture: it is a matter of proportions.” 

- Auto Layout in code: addConstraints with Visual Format Language

#### [Day 31](https://www.hackingwithswift.com/100/31)

> One of the three laws laid down by British science fiction writer Arthur C. Clarke is particularly well known: “any sufficiently advanced technology is indistinguishable from magic.”

- advanced Visual Formatting Language and Auto Layout anchors
- Every UIView has a set of anchors that define its layouts rules. The most important ones are widthAnchor, heightAnchor, topAnchor, bottomAnchor, leftAnchor, rightAnchor, leadingAnchor, trailingAnchor, centerXAnchor, and centerYAnchor.
- The “safe area” is the space that’s actually visible inside the insets of the iPhone X and other such devices – with their rounded corners, notch and similar. It’s a space that excludes those areas, so labels no longer run underneath the notch or rounded corners.

<hr>

####  [Day 32](https://www.hackingwithswift.com/100/32) - Consolidation III

> Chris Bosh, an NBA All-Star basketball player, said “every athlete knows that you get good by practicing, by repeating the same moves until you achieve your goal” 

## Codable, buttons, and GCD
## Project 7 - Whitehouse petitions
#### [Day 33](https://www.hackingwithswift.com/100/33)

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

#### [Day 34](https://www.hackingwithswift.com/100/34)

- injecting html code in detail view with  `webView.loadHTMLString(html, baseURL: nil)`
- Adding a second tapBarController in code

#### [Day 35](https://www.hackingwithswift.com/100/35) 
> Michelle Obama once said “through my education, I didn't just develop skills, I didn't just develop the ability to learn, but I developed confidence.”

- wrap up

## Project 8 - Build the layout in code - Swifty Words 
#### [Day 36](https://www.hackingwithswift.com/100/36)
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


#### [Day 37](https://www.hackingwithswift.com/100/37)
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
#### [Day 38](https://www.hackingwithswift.com/100/38)
> There are many well-known quotes from Shakespeare, but there’s one I think is particularly apt today: “the fool doth think he is wise, but the wise man knows himself to be a fool.”  


>In my talk at NSSpain 2018 I said “Auto Layout makes hard things easy, and easy things hard”   

## Project 9 - Grand Central Dispatch
#### [Day 39](https://www.hackingwithswift.com/100/39)
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


``` swift
// default Q
DispatchQueue.global().async { [weak self] in 
[...]
// or 

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

#### [Day 40](https://www.hackingwithswift.com/100/40)
> An old joke: " A programmer has a problem and thinks, “I can fix this using multitasking!” 
have Now problems! two they  

- race conditions are a whole category of bugs caused by one task completing before it was supposed to 
- GCD automatically handles thread creation and management, automatically balances based on available system resources, and automatically factors in Quality of Service 

## Consolidation IV
#### [Day 41](https://www.hackingwithswift.com/100/41)
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

## PROJECT 10 - Names to Faces 

#### [Day 42](https://www.hackingwithswift.com/100/42)
> my favorite quote from Douglas Adams: “I may not have gone where I intended to go, but I think I have ended up where I intended to be.”  

- `UICollectionViewController`, `UIImagePickerController`and `UUID`
- `fatalError()` always causes a crash, so we can it to escape from a method that has a return value without sending anything back
- `collectionView(_:numberOfItemsInSection:)`
- `collectionView(_:cellForItemAt:)`
- `dequeueReusableCell(withReuseIdentifier:for:)`

#### [Day 43](https://www.hackingwithswift.com/100/43)
> by the words of Valerie Plame: “Privacy is precious – I think privacy is the last true luxury. To be able to live your life as you choose without having everyone comment on it or know about.”

- `UIImagePickerController`
- Create a button `navigationItem.leftBarButtonItem = UIBarButtonItem(barButtonSystemItem: .add, target: self, action: #selector(addNewPerson))`
- this is the picker!
- We set the `allowsEditing` property to be `true`, which allows the user to crop the picture they select.
- When you set self as the delegate, you'll need to conform not only to the `UIImagePickerControllerDelegate` protocol, but also the `UINavigationControllerDelegate` protocol.
The whole method is being called from Objective-C code using `#selector`, so we need to use the `@objc` attribute

```swift
@objc func addNewPerson() {
    let picker = UIImagePickerController()
    picker.allowsEditing = true
    picker.delegate = self
    present(picker, animated: true)
}
```
 - The delegate method we care about is `imagePickerController(_, didFinishPickingMediaWithInfo:)`, which returns when the user selected an image and it's being returned to you. 

- we need to generate a unique filename for every image we import. We're going to use a new type for this, called `UUID`, which generates a Universally Unique Identifier 

```swift 
let imageName = UUID().uuidString
```
- All apps that are installed have a directory called Documents where you can save private information for the app, and it's also automatically synchronized with iCloud. The problem is, it's not obvious how to find that directory, so I have a method I use called getDocumentsDirectory() that does exactly that – you don't need to understand how it works, but you do need to copy it into your code.
``` swift
// ..
let imagePath = getDocumentsDirectory().appendingPathComponent(imageName)

    if let jpegData = image.jpegData(compressionQuality: 0.8) {
        try? jpegData.write(to: imagePath)
    }
//
func getDocumentsDirectory() -> URL {
        let paths = FileManager.default.urls(for: .documentDirectory, in: .userDomainMask)
        return paths[0]
    }


```

- NSObject is what's called a universal base class for all Cocoa Touch classes. That means all UIKit classes ultimately come from NSObject
- indexPath.item rather than indexPath.row
- round the cell amd i,age

``` swift
 cell.imageView.layer.borderColor = UIColor(white: 0, alpha: 0.3).cgColor
    cell.imageView.layer.borderWidth = 2
    cell.imageView.layer.cornerRadius = 3
    cell.layer.cornerRadius = 7

```


#### [Day 44](https://www.hackingwithswift.com/100/44)

- Wrap up and Challenge

## PROJECT 11 - Pachinko
#### [Day 45](https://www.hackingwithswift.com/100/45)

> Michael Jordan:“I’ve missed more than 9000 shots in my career. I've lost almost 300 games. 26 times, I've been trusted to take the game winning shot and missed. I've failed over and over and over again in my life. And that is why I succeed.”  

- SpriteKit is Apple’s high-performance drawing toolkit that lets us build advanced 2D games with relative ease.  
- in `GameScene.swift` replace with   

``` swift
import SpriteKit

class GameScene: SKScene {
    override func didMove(to view: SKView) {
    }

    override func touchesBegan(_ touches: Set<UITouch>, with event: UIEvent?) {
    }
}
```

- in the scene editor in the attributes inspector change the anchor point which should 0 for both X and Y.  
- SpriteKit considers Y:0 to be the bottom of the screen whereas UIKit considers it to be the top   
- iPad is 1024 points wide and 768 high  
- move the `Actions.sks` trash  
- If you want to place an image in your game, the class to use is called SKSpriteNode. To place the background image in the center of a landscape iPad, we need to place it at the position X:512, Y:384  
- And unlike UIKit SpriteKit positions things based on their center – i.e., the point 0,0 refers to the horizontal and vertical center of a node.  
- the blend mode .replace. Blend modes determine how a node is drawn, and SpriteKit gives you many options. The .replace option means "just draw it, ignoring any alpha values,"   
- give the background a zPosition of -1, which in our game means "draw this behind everything else."  
- add to  `didMove(to:)`   

``` swift
let background = SKSpriteNode(imageNamed: "background.jpg")
background.position = CGPoint(x: 512, y: 384)
background.blendMode = .replace
background.zPosition = -1
addChild(background)
```
- add to the `touchesBegan()` method. This method gets called (in UIKit and SpriteKit) whenever someone starts touching their device  

```swift
if let touch = touches.first {
    let location = touch.location(in: self)
    let box = SKSpriteNode(color: UIColor.red, size: CGSize(width: 64, height: 64))
    box.position = location
    addChild(box)
}
```
- UITouch is a UIKit class that is also used in SpriteKit, and provides information about a touch   

- Add a physicsBody. And just before the end of didMove(to:), add this:  

``` swift
box.physicsBody = SKPhysicsBody(rectangleOf: CGSize(width: 64, height: 64))
// and for the container
physicsBody = SKPhysicsBody(edgeLoopFrom: frame)
```
- We gonna now replace the boxes with balls  and add some bouncers    
- `ball.physicsBody = SKPhysicsBody(circleOfRadius: ball.size.width / 2.0)` 
- `ball.physicsBody?.restitution = 0.4`  restitution refers to bounciness
- `bouncer.physicsBody?.isDynamic = false`  object will not move upon collision


#### [Day 46](https://www.hackingwithswift.com/100/46)

> “In the beginning there was nothing, which exploded.” That’s a quote from Terry Pratchett’s book "Lords and Ladies"

- Angles are specified in radians, not degrees. This is true in UIKit too. 360 degrees is equal to the value of 2 x Pi – that is, the mathematical value π. Therefore π radians is equal to 180 degrees.  
- Rather than have you try to memorize it, there is a built-in value of π called CGFloat.pi.  
- CGFloat can be either a Double or a Float depending on the device your code runs on. Swift also has Double.pi and Float.pi for when you need it at different precisions.  
- When you create an action it will execute once. If you want it to run forever, you create another action to wrap the first using the repeatForever() method, then run that.  
- Apple recommends assigning names to your nodes  
- Add `physicsWorld.contactDelegate = self` for Collision detection
- Make our scene the contact delegate of the physics world – this means, "tell us when contact occurs between two bodies.  
- conform to the `SKPhysicsContactDelegate protocol` then assign the physics world's contactDelegate property to be our scene but still not enough. Need to do is change the `contactTestBitMask` property of our physics objects, which sets the contact notifications we want to receive.   
`ball.physicsBody!.contactTestBitMask = ball.physicsBody!.collisionBitMask `  
- we don't know what order it will come in. That is, did the ball hit the slot, did the slot hit the ball, or did both happen?

``` swift
func didBegin(_ contact: SKPhysicsContact) {
    guard let nodeA = contact.bodyA.node else { return }
    guard let nodeB = contact.bodyB.node else { return }

    if nodeA.name == "ball" {
        collisionBetween(ball: nodeA, object: nodeB)
    } else if nodeB.name == "ball" {
        collisionBetween(ball: nodeB, object: nodeA)
    }
}
```
- To make a score show on the screen we need to do two things: create a score integer that tracks the value itself, then create a new node type, SKLabelNode, that displays the value to players.  

``` swift
var scoreLabel: SKLabelNode!

var score = 0 {
    didSet {
        scoreLabel.text = "Score: \(score)"
    }
}
```

- a new property on nodes called zRotation, if you imagine sticking a skewer through the Z position – i.e., going directly into your screen – and through a node, then you can imagine Z rotation: it rotates a node on the screen   
- using both Int.random(in:) for integer values and CGFloat.random(in:) for CGFloat values, with the latter being used to create random red, green, and blue values for a UIColor.    
- The removeFromParent() method removes a node from your node tree.   

#### [Day 47](https://www.hackingwithswift.com/100/47)
> As Shakuntala Devi once said, “nobody challenges me – I challenge myself.”

- `SKEmitterNode class`
- play with the particle editor: `Particle Texture`: what image to use for your particles. `Particles Birthrate`: how fast to create new particles. `Particles Maximum`: the maximum number of particles this emitter should create before finishing. `Lifetime Start`: the basic value for how many seconds each particle should live for. `Lifetime Range`: how much, plus or minus, to vary lifetime. `Position Range X/Y`: how much to vary the creation position of particles from the emitter node's position. `Angle Start`: which angle you want to fire particles, in degrees, where 0 is to the right and 90 is straight up. `Angle Range`: how many degrees to randomly vary particle angle. `Speed Start`: how fast each particle should move in its direction. `Speed Range`: how much to randomly vary particle speed. `Acceleration X/Y`: how much to affect particle speed over time. This can be used to simulate gravity or wind. `Alpha Start`: how transparent particles are when created. `Alpha Range`: how much to randomly vary particle transparency. `Alpha Speed`: how much to change particle transparency over time. A negative value means "fade out." `Scale Start / Range / Speed`: how big particles should be when created, how much to vary it, and how much it should change over time. A negative value means "shrink slowly." `Rotation Start / Range / Speed`: what Z rotation particles should have, how much to vary it, and how much they should spin over time. `Color Blend Factor / Range / Speed`: how much to color each particle, how much to vary it, and how much it should change over time.

[REVIEW Project 11](https://www.hackingwithswift.com/review/hws/project-11-pachinko)

## PROJECT 12 - User Defaults

#### [Day 48](https://www.hackingwithswift.com/100/48)

> Douglas Adams once said, “most of the time spent wrestling with technologies that don't quite work yet is just not worth the effort for end users, however much fun it is for nerds like us.”

- NSCoding is a great way to read and write data when using UserDefaults, and is the most common option when you must write Swift code that lives alongside Objective-C code. if you’re only writing Swift, the Codable protocol is easier
- You can use UserDefaults to store any basic data type for as long as the app is installed. Max around 100K!

``` swift
let defaults = UserDefaults.standard
// write
defaults.set(25, forKey: "Age")
//When you're reading values from UserDefaults you need to check the return type carefully
let savedInteger = defaults.integer(forKey:"Age")

//and arrays too
let array = ["Hello", "World"]
defaults.set(array, forKey: "SavedArray")

let dict = ["Name": "Paul", "Country": "UK"]
defaults.set(dict, forKey: "SavedDict")

// to read need some objc
let array = defaults.object(forKey:"SavedArray") as? [String] ?? [String]()
let dict = defaults.object(forKey: "SavedDict") as? [String: String] ?? [String: String]()

```

- All your data types must be one of the following: boolean, integer, float, double, string, array, dictionary, Date.

- our data classes must conform to the NSCoding protocol, which is used for archiving object graphs and there is a required init to retrieve the data

``` swift
required init(coder aDecoder: NSCoder) {
name = aDecoder.decodeObject(forKey: "name") as? String ?? ""
image = aDecoder.decodeObject(forKey: "image") as? String ?? ""
}

func encode(with aCoder: NSCoder) {
aCoder.encode(name, forKey: "name")
aCoder.encode(image, forKey: "image")
}
```

- So we have our object and it conforms to NSCoding. There is the archivedData() method of NSKeyedArchiver which turns an object graph into a Data object which can be put in a dic in defaults. Then we can call self.save()

``` swift
// To save our people array of people objects..

func save() {
if let savedData = try? NSKeyedArchiver.archivedData(withRootObject: people, requiringSecureCoding: false) {
let defaults = UserDefaults.standard
defaults.set(savedData, forKey: "people")
}
}
```

- we retrieve the data first thing in viewDidLoad(): 
- First check if there is an object in defaults for our key, then try to decode it as [Person] if this is ok then use it ..

``` swift
let defaults = UserDefaults.standard

if let savedPeople = defaults.object(forKey: "people") as? Data {
    if let decodedPeople = try? NSKeyedUnarchiver.unarchiveTopLevelObjectWithData(savedPeople) as? [Person] {
    people = decodedPeople
    }
}
```

#### [Day 49](https://www.hackingwithswift.com/100/49)

> Alan Perlis once said “fools ignore complexity; pragmatists suffer it; some can avoid it; geniuses remove it.” Today you’re going to see that in Swift code: rather than try to simplify the code for NSCoding, the Swift team found a way to remove it entirely using the Codable protocol.

- You can use Codable instead of NSCoding in the class declaration if not using objc . it is so easy. going to use the JSONEncoder class to convert our people array into a Data object, which can then be saved to UserDefaults.

``` swift
func save() {
    let jsonEncoder = JSONEncoder()
    if let savedData = try? jsonEncoder.encode(people) {
        let defaults = UserDefaults.standard
        defaults.set(savedData, forKey: "people")
        } else {
        print("Failed to save people.")
        }
}

// and in view did load
let defaults = UserDefaults.standard

    if let savedPeople = defaults.object(forKey: "people") as? Data {
        let jsonDecoder = JSONDecoder()

    do {
        people = try jsonDecoder.decode([Person].self, from: savedPeople)
    } catch {
    print("Failed to load people")
        }
    }
```

[REVIEW Project 12](https://www.hackingwithswift.com/review/hws/project-12-userdefaults)

## MILESTONE: PROJECTS 10-12
#### [Day 50](https://www.hackingwithswift.com/100/50)

## Some element of functional programming
#### [Day 51](https://www.hackingwithswift.com/100/51)

>As Leonardo da Vinci said, “the noblest pleasure is the joy of understanding”

- learn about map(), flatMap(), filter()  

[Elements of Functional Programming](https://www.youtube.com/watch?v=OgU8d_E1K14)
[Teaching Swift at Scale](https://vimeo.com/291590798)

## PROJECT 13 - Instafilter
#### [Day 52](https://www.hackingwithswift.com/100/52)
> As Alexa Hirschfeld said, “the biggest challenge is to stay focused – to have the discipline when there are so many competing things.”

- See project 10 as well 
- We will use the `UIImagePickerController`
- add  `UIImagePickerControllerDelegate`,`UINavigationControllerDelegate`
- the first time you use a UIImagePickerController iOS will ask the user for permission to read their photo library, which means we need to add a text string describing our intent. So, open Info.plist add : Privacy - Photo Library Additions Usage Description
-  a new function: `UIImageWriteToSavedPhotosAlbum()`  

#### [Day 53](https://www.hackingwithswift.com/100/53)
> As Ben Shneiderman, a professor for Computer Science at the University of Maryland, once said, “a picture is worth a thousand words; an interface is worth a thousand pictures”

- we will use Core Image - Its API has never really been updated for Swift -Core Image is yet another super-fast and super-powerful framework from Apple. It does only one thing, which is to apply filters to images that manipulate them in various ways.  
- `import CoreImage`  
- add two more properties :
- `var context: CIContext!` this is the Core Image component that handles rendering  
- `var currentFilter: CIFilter!` This is a Core Image filter, and will store whatever filter the user has activated.  

```swift
// in the didFinishPickingMediaWithInfo method:

let beginImage = CIImage(image: currentImage)

currentFilter.setValue(beginImage, forKey: kCIInputImageKey)

// applyProcessing()
```

- The CIImage data type is, for the sake of this project, just the Core Image equivalent of UIImage.   

- this is the applyProcessing function.

```swift
func applyProcessing() {
    guard let image = currentFilter.outputImage else { return }
    currentFilter.setValue(intensity.value, forKey: kCIInputIntensityKey)

    if let cgimg = context.createCGImage(image, from: image.extent) {
        let processedImage = UIImage(cgImage: cgimg)
        imageView.image = processedImage
    }
}
```

- and the last two functions nescessary to save the image to the iphone

```swift 
@IBAction func save(_ sender: Any) {
guard let image = imageView.image else { return }

UIImageWriteToSavedPhotosAlbum(image, self, #selector(image(_:didFinishSavingWithError:contextInfo:)), nil)
}

@objc func image(_ image: UIImage, didFinishSavingWithError error: Error?, contextInfo: UnsafeRawPointer) {
    if let error = error {
    // we got back an error!
    let ac = UIAlertController(title: "Save error", message: error.localizedDescription, preferredStyle: .alert)
    ac.addAction(UIAlertAction(title: "OK", style: .default))
    present(ac, animated: true)
    } else {
    let ac = UIAlertController(title: "Saved!", message: "Your altered image has been saved to your photos.", preferredStyle: .alert)
    ac.addAction(UIAlertAction(title: "OK", style: .default))
    present(ac, animated: true)
}
}
```


#### [Day 54](https://www.hackingwithswift.com/100/54)

[Review project 13](https://www.hackingwithswift.com/review/hws/project-13-instafilter)

## Project 14 - Whack a Penguin
#### [Day 55](https://www.hackingwithswift.com/100/55)
> Ezra Koenig said “some people say video games rot your brain, but I think they work different muscles that maybe you don't normally use.”

- `SKCropNode`  This is a special kind of `SKNode` subclass that uses an image as a cropping mask: anything in the colored part will be visible, anything in the transparent part will be invisible.  
- `let cropNode = SKCropNode()`  
- you create a cropnode. the position will be relative to the parent.. position is on top. Create a character node as sprite node with image, position it relative to parent and add as crop node child. then add the crop node. The mask node will be a sprite node with a mask image where the transparent parts will not be shown and will cover our character.

```swift
let cropNode = SKCropNode()
cropNode.position = CGPoint(x: 0, y: 15)
cropNode.zPosition = 1
cropNode.maskNode = SKSpriteNode(imageNamed: "whackMask")

charNode = SKSpriteNode(imageNamed: "penguinGood")
charNode.position = CGPoint(x: 0, y: -90)
charNode.name = "character"
cropNode.addChild(charNode)

addChild(cropNode)
```

- `SKAction`, called  `moveBy(x:y:duration:)`    
- `charNode.run(SKAction.moveBy(x: 0, y: 80, duration: 0.05))`    
- We can change the image inside our penguin sprite by changing its texture property. This takes a new class called `SKTexture`   
- delay :  some new Grand Central Dispatch (GCD) code: asyncAfter() is used to schedule a closure to execute after the time has been reached  
```swift
DispatchQueue.main.asyncAfter(deadline: .now() + 1) { [weak self] in
    self?.doStuff()
}
```

#### [Day 56](https://www.hackingwithswift.com/100/56)

> Marie Curie, the only person in history to win the Nobel prize in two different sciences, once said, “I was taught that the way of progress was neither swift nor easy.”

- `SKAction`  
- `SKAction.wait(forDuration:)` creates an action that waits for a period of time, measured in seconds.  
- `SKAction.run(block:)' will run any code we want, provided as a closure. "Block" is Objective-C's name for a Swift closure.  
- `SKAction.sequence()`  takes an array of actions, and executes them in order. Each action won't start executing until the previous one finished.  
- The code to hide a penguin  

```swift
let delay = SKAction.wait(forDuration: 0.25)
let hide = SKAction.moveBy(x: 0, y: -80, duration: 0.5)
let notVisible = SKAction.run { [unowned self] in self.isVisible = false }
charNode.run(SKAction.sequence([delay, hide, notVisible]))
}
```
- in the function `touchesBegan()` we check where we touched and see if we got a whackSlot with the below    
- `guard let whackSlot = node.parent?.parent as? WhackSlot else { continue }`  
- `SKAction`'s  `playSoundFileNamed()` method  
- `caf` is a renamed `aiff` file. AIFF is a pretty terrible file format when it comes to file size, but it's much faster to load and use than MP3s and M4As  
- ex `run(SKAction.playSoundFileNamed("whackBad.caf", waitForCompletion: false))`

[Review Project 14](https://www.hackingwithswift.com/review/hws/project-14-whack-a-penguin)

## PROJECT 15 - Animation
#### [Day 57](https://www.hackingwithswift.com/100/57)
> John Maeda, design lead at Automattic (the company behind Wordpress), put this rather succinctly: “Design used to be the seasoning you’d sprinkle on for taste; now it’s the flour you need at the start of the recipe.”    

- we add an image to the view:

```swift
imageView = UIImageView(image: UIImage(named: "penguin"))
imageView.center = CGPoint(x: 512, y: 384)
view.addSubview(imageView)
```

- we want to hide the button during the animation. to do so we pass the UIButton in sender..

``` swift
@IBAction func tapped(_ sender: UIButton) {
sender.isHidden = true
```
- we gonna use this funtion of UIView: `UIView.animate(withDuration: <#T##TimeInterval#>, delay: <#T##TimeInterval#>, options: <#T##UIView.AnimationOptions#>, animations: <#T##() -> Void#>, completion: <#T##((Bool) -> Void)?##((Bool) -> Void)?##(Bool) -> Void#>)`    
- in code we pass two closures:

```swift
UIView.animate(withDuration: 1, delay: 0, options: [], 
    animations: {
        switch self.currentAnimation {
        case 0:
            break

        default:
            break
            }
    }) { finished in
        sender.isHidden = false
}
```

- in the animation closure we put code to be execute.  
- `CGAffineTransform`. This is a structure that represents a specific kind of transform that we can apply to any `UIView` object or subclass.
- ex  `self.imageView.transform = CGAffineTransform(scaleX: 2, y: 2)`  
- ex `self.imageView.transform = CGAffineTransform(translationX: -256, y: -256)`  

- return to original value `self.imageView.transform = .identity` This effectively clears our view of any pre-defined transform  
- We can also use CGAffineTransform to rotate views, using its rotationAngle initializer. `self.imageView.transform = CGAffineTransform(rotationAngle: CGFloat.pi)` . Core Animation will always take the shortest route to make the rotation work.   


#### [Day 58](https://www.hackingwithswift.com/100/58)
> Larry Niven once said, “that's the thing about people who think they hate computers – what they really hate is lousy programmers.”

- wrap up and [review project 15](https://www.hackingwithswift.com/review/hws/project-15-animation)  

## MILESTONE: PROJECTS 13-15
#### [Day 59](https://www.hackingwithswift.com/100/59)
> As Anthony J. D'Angelo once said, “develop a passion for learning – if you do, you will never cease to grow.”

## PROJECT 16 - Capital Cities
#### [Day 60](https://www.hackingwithswift.com/100/60)
> Do you remember when the iPhone was announced? Seeing Steve Jobs show us on-device maps for the first time was incredible – after at least a decade of maps seeming like dusty old things we can safely ignore, suddenly mapping was cool again  

- adding a map is so easy : in storyboard , search for "map" in the object library, drop a map view into your view controller so that it occupies the full view, then use `Resolve Auto Layout Issues > Add Missing Constraints` so that it stays next to each edge.  Now, run your program and you should see a basic map working nicely.
- `import MapKit`
- ctrl - drag from `mapView` to the viewController file and create an outlet. then ctrl - drag to the viewController in panel and choose `delegate`  !!
- `Annotations` are objects that contain a title, a subtitle and a position. The first two are both strings, the third is a new data type called `CLLocationCoordinate2D` , which is a structure that holds a latitude and longitude for where the annotation should be placed  
- Map annotations are described not as a class, but as a protocol.
- we want to conform to the `MKAnnotation` protocol  
- With map annotations, you can't use structs, and you must inherit from `NSObject` because it needs to be interactive with Apple's Objective-C code.

```swift
import MapKit
import UIKit

class Capital: NSObject, MKAnnotation {
    var title: String?
    var coordinate: CLLocationCoordinate2D
    var info: String

    init(title: String, coordinate: CLLocationCoordinate2D, info: String) {
        self.title = title
        self.coordinate = coordinate
        self.info = info
}
}
```

- adding a point will be easy in `viewDidLoad()`, ex: `let london = Capital(title: "London", coordinate: CLLocationCoordinate2D(latitude: 51.507222, longitude: -0.1275), info: "Home to the 2012 Summer Olympics.")`  
- and `mapView.addAnnotation(london)` 
-  Every time the map needs to show an annotation, it calls a `viewFor` method on its delegate.   
- Customizing an annotation view is a little bit like customizing a table view cell or collection view cell, because iOS automatically reuses annotation views to make best use of memory. If there isn't one available to reuse, we need to create one from scratch using the `MKPinAnnotationView` class.
- If an annotation is not one of yours, just return nil from the method to have Apple's default used instead  
- add `MKMapViewDelegate` n your code   

```swift
func mapView(_ mapView: MKMapView, viewFor annotation: MKAnnotation) -> MKAnnotationView? {
    // If the annotation isn't from a capital city, it must return nil so iOS uses a default view.
    guard annotation is Capital else { return nil }

    // Define a reuse identifier
    let identifier = "Capital"

    // Try to dequeue
    var annotationView = mapView.dequeueReusableAnnotationView(withIdentifier: identifier)

    if annotationView == nil {
    // or create a new one using MKPinAnnotationView which sets its canShowCallout property to true. This triggers the popup with the city name.
    annotationView = MKPinAnnotationView(annotation: annotation, reuseIdentifier: identifier)
    annotationView?.canShowCallout = true

    // Create a new UIButton using the built-in .detailDisclosure type. This is a small blue "i" symbol with a circle around it.
    let btn = UIButton(type: .detailDisclosure)
    annotationView?.rightCalloutAccessoryView = btn
    } else {
    // 6
    annotationView?.annotation = annotation
}
// and use the calloutAccessoryControlTapped method. The annotation view contains a property called annotation, which will contain our Capital object. So, we can pull that out, typecast it as a Capital, then show its title and information in any way we want. The easiest for now is just to use a UIAlertController, so that's what we'll do.


func mapView(_ mapView: MKMapView, annotationView view: MKAnnotationView, calloutAccessoryControlTapped control: UIControl) {
    guard let capital = view.annotation as? Capital else { return }
    let placeName = capital.title
    let placeInfo = capital.info

    let ac = UIAlertController(title: placeName, message: placeInfo, preferredStyle: .alert)
    ac.addAction(UIAlertAction(title: "OK", style: .default))
    present(ac, animated: true)
    }

    return annotationView
}
```
- and thats it!  


#### [Day 61](https://www.hackingwithswift.com/100/61)

- wrap up and [review project 16](https://www.hackingwithswift.com/review/hws/project-16-capital-cities)

## PROJECT 17 - Space Race

- this is already most of the code:

```swift
override func didMove(to view: SKView) {
    backgroundColor = .black

    starfield = SKEmitterNode(fileNamed: "starfield")!
    starfield.position = CGPoint(x: 1024, y: 384)
    starfield.advanceSimulationTime(10)
    addChild(starfield)
    starfield.zPosition = -1

    player = SKSpriteNode(imageNamed: "player")
    player.position = CGPoint(x: 100, y: 384)
    player.physicsBody = SKPhysicsBody(texture: player.texture!, size: player.size)
    player.physicsBody?.contactTestBitMask = 1
    addChild(player)

    scoreLabel = SKLabelNode(fontNamed: "Chalkduster")
    scoreLabel.position = CGPoint(x: 16, y: 16)
    scoreLabel.horizontalAlignmentMode = .left
    addChild(scoreLabel)

    score = 0

    physicsWorld.gravity = CGVector(dx: 0, dy: 0)
    physicsWorld.contactDelegate = self
}
```

- this disables gravity : `physicsWorld.gravity = CGVector(dx: 0, dy: 0)` or  `physicsWorld.gravity = .zero`  

- and need to conform to the `SKPhysicsContactDelegate`  
- We need a timer `var gameTimer: Timer?` When you create an Timer you specify five parameters: how many seconds you want the delay to be, what object should be told when the timer fires, what method should be called on that object when the timer fires, any context you want to provide, and whether the time should repeat.  
- `gameTimer = Timer.scheduledTimer(timeInterval: 0.35, target: self, selector: #selector(createEnemy), userInfo: nil, repeats: true)`  
- `linearDamping` and `angularDamping` properties, which mean movement and rotation slowing down over time  
- there is a builtin function update... `override func update(_ currentTime: TimeInterval) { // Called before each frame is rendered }` here I will update the score and destroy the sprites which went past our player ...
- To move our player we implement the `touchesMoved()` method with `guard let touch = touches.first else { return }; 
var location = touch.location(in: self)`  
- When there is a collision: `func didBegin(_ contact: SKPhysicsContact) { //explosion! } `  we remore the player and add emitter particles  

#### [Day 62](https://www.hackingwithswift.com/100/62)
> Fred Brooks, who wrote the seminal book The Mythical Man-Month: "Plan to throw the first one away.”

#### [Day 63](https://www.hackingwithswift.com/100/63)
> As Mahatma Gandhi said, “An ounce of practice is worth more than tons of preaching.”  

[Review project 17](https://www.hackingwithswift.com/review/hws/project-17-space-race)

## PROJECT 18 - Debugging
#### [Day 64](https://www.hackingwithswift.com/100/64)
> Thomas Fuchs once said, “the best error message is the one that never shows up.”   

>“Debugging is twice as hard as writing the code in the first place. Therefore, if you write the code as cleverly as possible, you are, by definition, not smart enough to debug it.”

- the absolute easiest debugging technique, which is the `print()` function  
- `print(1, 2, 3, 4, 5, separator: "-")` and `print("Some message", terminator: "")` (terminator is by default "\n")  
- One level up from print() are `assertions`, which are debug-only checks that will force your app to crash if a specific condition isn't true.  When you build a release version of your app – i.e., when you ship your app to the App Store – Xcode automatically disables your assertions so they won’t reach your users  
- ex `assert(1 == 1, "Maths failure!")`  
- `breakpoints`  
- Xcode also gives you an interactive LLDB debugger window, where you can type commands to query values and run methods. Try typing `p` `i` to ask Xcode to print the value of the `i` variable   
-  in Xcode go to the `Debug` menu and choose `View Debugging > Capture View Hierarchy`. After a few seconds of thinking, Xcode will show you a screenshot of your app’s UI. if you click and drag inside the hierarchy display, you'll see you're actually viewing a 3D representation of your view  

#### [Day 65](https://www.hackingwithswift.com/100/65)

[Review project 18](https://www.hackingwithswift.com/review/hws/project-18-debugging)

## MILESTONE: PROJECTS 16-18

#### [Day 66](https://www.hackingwithswift.com/100/66)
> As Dan Millman said, “willpower is the key to success – successful people strive no matter what they feel by applying their will to overcome apathy, doubt or fear.”  

## PROJECT 19 - JS Injection
#### [Day 67](https://www.hackingwithswift.com/100/67)
> Ginni Rometty once said: "what I knew was I liked math and science, and I never wanted to memorize everything – I wanted to understand where it came from"

- Safari extensions are launched from within the Safari action menu, but they ship inside a parent app. That is, you can't ship an extension by itself – it needs have an app alongside it. Frequently the app does very little, but it must at least be present.  
- go to the `File` menu and choose `New > Target`. When you're asked to choose a template, select `iOS > Application Extension > Action Extension  
- Xcode has given you two files: `ActionViewController.swift` and `MainInterface.storyboard`.  
-  When our extension is created, its `extensionContext` lets us control how it interacts with the parent app. In the case of `inputItems` this will be an array of data the parent app is sending to our extension to use.  
- Our input item contains an array of attachments, which are given to us wrapped up as an `NSItemProvider`. Our code pulls out the first attachment  
- The next line uses `loadItem(forTypeIdentifier: )` to ask the item provider to actually provide us with its item, but you'll notice it uses a closure so this code executes asynchronously.      

``` swift 
if let inputItem = extensionContext?.inputItems.first as? NSExtensionItem {
    if let itemProvider = inputItem.attachments?.first {
        itemProvider.loadItem(forTypeIdentifier: kUTTypePropertyList as String) { 
            [weak self] (dict, error) in
            // do stuff!
            }
        }
}
```

- inside the extension group there is a `plist` (that's short for property list, remember) contains metadata about apps and extensions  
- in plist editor look for `NSExtension` and `NSExtensionAttributes` and  `NSExtensionActivationRule`, set to `TRUEPREDICATE`. Change string to be Dictionary, then open its disclosure arrow and click the small + button to the left of “Dictionary”, and when it asks you for a key name change "New item" to be `NSExtensionActivationSupportsWebPageWithMaxCount` with value `1` . We only want to receive webpages.  
- click again on + and add `NSExtensionJavaScriptPreprocessingFile` , then give it the value `Action`. This tells iOS that when our extension is called, we need to run the JavaScript preprocessing file called `Action.js`   
- Right-click on your extension's `Info.plist` file and choose `New File`. When you're asked what template you want, choose `iOS > Other > Empty`, then name it Action.js, and put this text into it: 

``` js
var Action = function() {};

Action.prototype = {

run: function(parameters) {

},

finalize: function(parameters) {

}

};

var ExtensionPreprocessingJS = new Action
```

- There are two functions: run() and finalize(). The first is called before your extension is run, and the other is called after.
- check under `extension` `build phases`  . you should see Action.js under `Copy Bundle Resources` and not `Compile Sources`. If this isn't the case, you can just drag it to move.  

#### [Day 68](https://www.hackingwithswift.com/100/68)
> As Jeremy Foster once said, “every developer loves and hates JavaScript a little bit”

- The point of this project isn’t to teach you JavaScript, but instead to show you what’s possible with iOS  
- Go to Action.js and modify the run() function to this:  

``` js
run: function(parameters) {
parameters.completionFunction({"URL": document.URL, "title": document.title });
},
```

- Now that data is being sent from JavaScript, data will be received in Swift. In ActionViewController.swift, replace the // do stuff! comment with this:  

``` swift
guard let itemDictionary = dict as? NSDictionary else { return }
guard let javaScriptValues = itemDictionary[NSExtensionJavaScriptPreprocessingResultsKey] as? NSDictionary else { return }
print(javaScriptValues)
```

-  `UITextField` it's useful for letting users enter text into a single-line text box. But if you want multiple lines of text you need `UITextView`  
- [ ... phew check on the web for more.. basically we input JS and it will be executed on the site ...]

- We can ask to be told when the keyboard state changes by using a new class called NotificationCenter. Behind the scenes, iOS is constantly sending out notifications when things happen – keyboard changing, application moving to the background, as well as any custom events that applications post. We can add ourselves as an observer for certain notifications and a method we name will be called when the notification occurs, and will even be passed any useful information.  
- When working with the keyboard, the notifications we care about are `keyboardWillHideNotification` and `keyboardWillChangeFrameNotification`. The first will be sent when the keyboard has finished hiding, and the second will be shown when any keyboard state change happens – including showing and hiding, but also orientation, QuickType and more.  
- add this code to 'viewDidLoad()':  

```swift
let notificationCenter = NotificationCenter.default
notificationCenter.addObserver(self, selector: #selector(adjustForKeyboard), name: UIResponder.keyboardWillHideNotification, object: nil)
notificationCenter.addObserver(self, selector: #selector(adjustForKeyboard), name: UIResponder.keyboardWillChangeFrameNotification object: nil)
```

- The `adjustForKeyboard()` method is complicated, but that's because it has quite a bit of work to do. First, it will receive a parameter that is of type Notification. This will include the name of the notification as well as a Dictionary containing notification-specific information called userInfo.  

- When working with keyboards, the dictionary will contain a key called `UIResponder.keyboardFrameEndUserInfoKey` telling us the frame of the keyboard after it has finished animating. This will be of type `NSValue`, which in turn is of type `CGRect`. The `CGRect` struct holds both a `CGPoint` and a `CGSize`, so it can be used to describe a rectangle.  
- One of the quirks of Objective-C was that arrays and dictionaries couldn't contain structures like CGRect, so Apple had a special class called NSValue that acted as a wrapper around structures so they could be put into dictionaries and arrays.    

- look for the `function text view insets for keyboards ` on the website!!

#### [Day 69](https://www.hackingwithswift.com/100/69)

wrap up! [Review Project 19](https://www.hackingwithswift.com/review/hws/project-19-javascript-injection)

## PROJECT 20 - Fireworks Night
#### [Day 70](https://www.hackingwithswift.com/100/70)

>When Steve Jobs first announced the iPhone, he asked an important question: “how are we going to communicate with this?” His answer was as follows: “We don’t want to carry around a mouse, right? So what are we going to do? Oh, a stylus, right? We’re going to use a stylus. No! Who wants a stylus? You have to get them and put them away, and you lose them – yuck. Nobody wants a stylus, so we’re not going to use a stylus. We’re going to use the best pointing device in the world. We’re going to use a pointing device we’re all born with, we’re born with ten of them – we’re going to use our fingers.”  

- create a timer firing every 6 sec `gameTimer = Timer.scheduledTimer(timeInterval: 6, target: self, selector: #selector(launchFireworks), userInfo: nil, repeats: true)`  
-  two new properties: `color` and `colorBlendFactor`. These two show off a simple but useful feature of `SpriteKit`, which is its ability to recolor your sprites dynamically with absolutely no performance cost. So, our rocket image is actually white, but by giving it `.red` with `colorBlendFactor` set to 1 (use the new color exclusively) it will appear red.  
-  a new `SKAction` you haven't seen before: `follow()`. This takes a `CGPath` as its first parameter (we'll pull this from the `UIBezierPath`) and makes the node move along that path. It doesn't have to be a straight line like we're using, any bezier path is fine.  

```swift
let path = UIBezierPath()
path.move(to: .zero)
path.addLine(to: CGPoint(x: xMovement, y: 1000))

// 5
let move = SKAction.follow(path.cgPath, asOffset: true, orientToPath: true, speed: 200)
node.run(move)

```

- The `follow()` method takes three other parameters, all of which are useful. The first decides whether the path coordinates are absolute or are relative to the node's current position. If you specify `asOffset` as true, it means any coordinates in your path are adjusted to take into account the node's position.  
- The third parameter to `follow()` is `orientToPath` and makes a complicated task into an easy one. When it's set to true, the node will automatically rotate itself as it moves on the path so that it's always facing down the path. Perfect for fireworks, and indeed most things! Finally, you can specify a speed to adjust how fast it moves along the path.   
-  a new piece of Swift syntax  `for case let`  
- our built in functions `touchesBegan()` and `touchesMoved()`  
- You see, when we ask for all the nodes under the users finger we’ll get back an array of SKNode, and that’s not good enough we want to run the body of our loop only for sprite nodes, not for the other items.  
- `for case let node as SKSpriteNode in nodesAtPoint {`   : The let node part creates a new constant called node, the case…as SKSpriteNode part means “if we can typecast this item as a sprite node  


#### [Day 71](https://www.hackingwithswift.com/100/71)
> John Gruber recounts an anecdote he heard about how shake to undo came about, which might why it just doesn’t fit in with the rest of the platform: "Scott Forstall charged the iOS team with devising an interface for Undo — everyone knew the iPhone should have it,1 but no one had a good idea how to do it. One engineer joked that they could just make you shake the iPhone to invoke it. Forstall said he loved the idea, and what was proposed as a joke has been with us as the Undo interface ever since.  

[PROJECT 20 Review](https://www.hackingwithswift.com/review/hws/project-20-fireworks-night)

## PROJECT 21 - Local Notifications
#### [Day 72](https://www.hackingwithswift.com/100/72)
> Tim Ferriss is a well-known podcaster and angel investor, who once said “in a digital world, there are numerous technologies that we are attached to that create infinite interruption.”

- `import UserNotifications`
-  request auth 

```swift
@objc func registerLocal() {
    let center = UNUserNotificationCenter.current()

    center.requestAuthorization(options: [.alert, .badge, .sound]) { (granted, error) in
        if granted {
            print("Yay!")
            } else {
            print("D'oh")
        }
    }
}
```

- the trigger – when to show the notification – can be a calendar trigger that shows the notification at an exact time, it can be an interval trigger that shows the notification after a certain time interval has lapsed, or it can be a geofence that shows the notification based on the user’s location.  
- new data type called `DateComponents`.

``` swift
var dateComponents = DateComponents()
dateComponents.hour = 10
dateComponents.minute = 30
let trigger = UNCalendarNotificationTrigger(dateMatching: dateComponents, repeats: true)
```  

- what to show, we need to use the class `UNMutableNotificationContent`  
- This class got `title` property , `body` property, `sound` property with `UNNotificationSound.default` , `userInfo` dictionary property and custom actions by specifying the `categoryIdentifier` property.  

- ex

```swift
@objc func scheduleLocal() {
let center = UNUserNotificationCenter.current()

let content = UNMutableNotificationContent()
content.title = "Late wake up call"
content.body = "The early bird catches the worm, but the second mouse gets the cheese."
content.categoryIdentifier = "alarm"
content.userInfo = ["customData": "fizzbuzz"]
content.sound = UNNotificationSound.default

var dateComponents = DateComponents()
dateComponents.hour = 10
dateComponents.minute = 30
let trigger = UNCalendarNotificationTrigger(dateMatching: dateComponents, repeats: true)

let request = UNNotificationRequest(identifier: UUID().uuidString, content: content, trigger: trigger)
center.add(request)
}
````

 - cancel pending notifications `center.removeAllPendingNotificationRequests()`
 -  two new classes: `UNNotificationAction` creates an individual button for the user to tap, and `UNNotificationCategory` groups multiple buttons together under a single identifier.  
 - need to add `UNUserNotificationCenterDelegate`
 

#### [Day 73](https://www.hackingwithswift.com/100/73)
> “if privacy matters in your life, it should matter to the phone your life is on.” 

[PROJECT 21 Review](https://www.hackingwithswift.com/review/hws/project-21-local-notifications)


## MILESTONE: PROJECTS 19-21
#### [Day 74](https://www.hackingwithswift.com/100/74)
>Henry Petroski, a professor of engineering at Duke University in the US, said “as engineers, we’re going to be in a position to change the world, not just study it.” 


## PROJECT 22 - 
#### [Day 75](https://www.hackingwithswift.com/100/75)

> As Phyllis Schlafly said, “location is the key to most businesses, and the entrepreneurs typically build their reputation at a particular spot.”

Apple introduced iBeacon technology with iOS 7, already a long time ago!
 I recommend you install the app "Locate Beacon" on your iPad or iPhone, because that comes with an iBeacon transmitter built in, making it perfect for testing. 
Need an iOS device that's compatible with iBeacons, which means iPhone 5 or later, 3rd generation iPad or later. the iOS Simulator won't work.  

You're creating an app that needs to be woken up when the user reaches a location. You need access even when the app isn't running. It is a privacy concern.

Apple flags it up in three ways:

- If you request Always access, users will still get the chance to choose When In Use.   
- If they choose Always, iOS will automatically ask them again after a few days to confirm they still want to grant Always access.  
- When your app is using location data in the background the iOS UI will update to reflect that – users will know it’s happening.  
- Users can, at any point, go into the settings app and change from Always down to When In Use.  

This requires a change to your apps Info.plist file.  And then you will need:  


``` swift
import CoreLocation
// This is the Core Location class that lets us configure how we want to be notified about location, and will also deliver location updates to us.
var locationManager: CLLocationManager?

//create the object , then set ourselves as its delegate (easy, but we need to conform to the protocol), then finally we need to request authorization
class ViewController: UIViewController, CLLocationManagerDelegate {
override func viewDidLoad() {
    super.viewDidLoad()

    locationManager = CLLocationManager()
    locationManager?.delegate = self
    locationManager?.requestAlwaysAuthorization()

}
```

Requesting location authorization is a non-blocking call, When the user has finally made their mind, you'll get told their result because we set ourselves as the delegate for our CLLocationManager object. The method that will be called is this one:  
``` swift
func locationManager(_ manager: CLLocationManager, didChangeAuthorization status: CLAuthorizationStatus) {
    if status == .authorizedAlways {
        if CLLocationManager.isMonitoringAvailable(for: CLBeaconRegion.self) {
            if CLLocationManager.isRangingAvailable() {
                // do stuff
            }
        }
    }
}
```
we use a new class called `CLBeaconRegion`, which is used to identify a beacon uniquely. Second, we give that to our `CLLocationManager` object by calling its `startMonitoring(for:)` and `startRangingBeacons(in:)` methods.

`iBeacons` are identified using three pieces of information: a `universally unique identifier` : `UUID`, plus a major number and a minor number. The first number is a long hexadecimal string that you can create by running the `uuidgen` in your Mac's terminal. The major number is used to subdivide within the UUID. So, if you have 10,000 stores in your supermarket chain, you would use the same UUID for them all but give each one a different major number. That major number must be between 1 and 65535, The minor number can (if you wish) be used to subdivide within the major number

``` swift
func startScanning() {
    let uuid = UUID(uuidString: "5A4BCFCE-174E-4BAC-A814-092E77F6B7E5")!
    let beaconRegion = CLBeaconRegion(proximityUUID: uuid, major: 123, minor: 456, identifier: "MyBeacon")

    locationManager?.startMonitoring(for: beaconRegion)
    locationManager?.startRangingBeacons(in: beaconRegion)
}
// and this updating us on the results
func update(distance: CLProximity) {
    UIView.animate(withDuration: 1) {
        switch distance {
            case .unknown:
            case .far:
            case .near:
            case .immediate:
            @unknown default:
            }
}
}
// and here is the last piece of code needed
func locationManager(_ manager: CLLocationManager, didRangeBeacons beacons: [CLBeacon], in region: CLBeaconRegion) {
    if let beacon = beacons.first {
        update(distance: beacon.proximity)
    } else {
        update(distance: .unknown)
        }
}
```


#### [Day 76](https://www.hackingwithswift.com/100/76)
> Mo Farah – multiple-time British Olympic gold medallist – said “if you dream and have the ambition and want to work hard, then you can achieve.” 

[Wrap up](https://www.hackingwithswift.com/review/hws/project-22-detect-a-beacon) 

## PROJECT 23 - Swifty Ninja
#### [Day 77](https://www.hackingwithswift.com/100/77)
> Winston Churchill once said, “success is not final, failure is not fatal: it is the courage to continue that counts.”

Drawing a shape in SpriteKit is easy thanks to a special node type called `SKShapeNode`. This lets you define any kind of shape you can draw, along with line width, stroke color and more, and it will render it to the screen.

We're going to keep an array of the user's swipe points so that we can draw a shape resembling their slicing. To make this work, we're going to need four new methods, two of which you've met already. They are: touchesBegan(), touchesMoved(), touchesEnded() and redrawActiveSlice().  
we can store swipe points:  

``` swift
var activeSlicePoints = [CGPoint]()

override func touchesMoved(_ touches: Set<UITouch>, with event: UIEvent?) {
    guard let touch = touches.first else { return }
    let location = touch.location(in: self)
    activeSlicePoints.append(location)
    redrawActiveSlice()
}

override func touchesEnded(_ touches: Set<UITouch>, with event: UIEvent?) {
    activeSliceBG.run(SKAction.fadeOut(withDuration: 0.25))
    activeSliceFG.run(SKAction.fadeOut(withDuration: 0.25))
}
```

This is how we draw keeping 12 points in the array with a Bezier path!

``` swift
func redrawActiveSlice() {
// If we have fewer than two points in our array, we don't have enough data to draw a line so it needs to clear the shapes and exit the method.
if activeSlicePoints.count < 2 {
    activeSliceBG.path = nil
    activeSliceFG.path = nil
return
}

// If we have more than 12 slice points in our array, we need to remove the oldest ones until we have at most 12
if activeSlicePoints.count > 12 {
    activeSlicePoints.removeFirst(activeSlicePoints.count - 12)
}

// It needs to start its line at the position of the first swipe point, then go through each of the others drawing lines to each point.
let path = UIBezierPath()
    path.move(to: activeSlicePoints[0])

for i in 1 ..< activeSlicePoints.count {
    path.addLine(to: activeSlicePoints[i])
}

// update the slice shape paths so they get drawn using their designs – i.e., line width and color.
activeSliceBG.path = path.cgPath
activeSliceFG.path = path.cgPath
}
```

The sounds! We want only one swoosh to play at once, so we're going to set to true a property called isSwooshSoundActive, make the waitForCompletion of our SKAction true, then use a completion closure for runAction() so that isSwooshSoundActive is set to false.  

``` swift
func playSwooshSound() {
    isSwooshSoundActive = true

    let randomNumber = Int.random(in: 1...3)
    let soundName = "swoosh\(randomNumber).caf"

    let swooshSound = SKAction.playSoundFileNamed(soundName, waitForCompletion: true)

    run(swooshSound) { [weak self] in
        self?.isSwooshSoundActive = false
    }
}
```

 Creating a bomb also needs to play a fuse sound, but that has its own complexity. You've already seen that SKAction has a very simple way to play sounds, but it's so simple that it's not useful here  
 That solution is called AVAudioPlayer, and it's not a SpriteKit class – it's available to use in your UIKit apps too if you want. We're going to have an AVAudioPlayer property for our class that will store a sound just for bomb fuses so that we can stop it as needed.  
 
 A new protocol : CaseIterable. This is one of Swift’s most useful protocols.
 
 ```swift
 enum SequenceType: CaseIterable {
    case oneNoBomb, one, twoWithOneBomb, two, three, four, chain, fastChain
 }
 ```
 we can then use randomElement() to pick random sequence types to run our game.   So, to generate lots of random sequence types we can use SequenceType.allCases.randomElement() again and again.  Making an enum conform to CaseIterable will give it an allCases array.
 This property is automatically generated by the compiler, and features all cases in the order they were listed in your own.  
 
 
 
#### [Day 78](https://www.hackingwithswift.com/100/78)
> as Thomas Edison once said, “the most certain way to succeed is always to try just one more time.”

#### [Day 79](https://www.hackingwithswift.com/100/79)
> Shigeru Miyamoto – the legendary Japanese game designer who gave us Mario, Zelda, Donkey Kong, and more – once said “to create a new standard, you have to be up for that challenge and really enjoy it.”   

[Wrap up and challenges](https://www.hackingwithswift.com/review/hws/project-23-swifty-ninja)

## PROJECT 24 - Swift Strings

#### [Day 80](https://www.hackingwithswift.com/100/80)
> Steve Jobs famously said “this is what customers pay us for: to sweat all these details so it's easy and pleasant for them to use our computers,” and strings are a good example of one of those details – they look like they ought to be simple, but if you want to get them right you need to spend some time working at it.  

There’s more to strings than just being a sequence of characters. In fact, Swift’s string handling is the most advanced I’ve seen in any language, and as a result if you play by Swift’s rules you’ll find your apps work great in every conceivable language – something that most developers for other languages need to work hard at.
`NSAttributedString`  Supported for attributed strings is baked into most of UIKit, so you can use it with UILabel, UITextView, and more.

``` swift
let name = "Taylor"

for letter in name {
    print("Give me a \(letter)!"
}
// this wont work
print(name[3])
```
Letters in a string aren’t just a series of alphabetical characters – they can contain accents such as á, é, í, ó, or ú, they can contain combining marks that generate wholly new characters by building up symbols, or they can even be emoji.  

```swift
let letter = name[name.index(name.startIndex, offsetBy: 3)]
```
Also `reading name.count` isn’t a quick operation: Swift literally needs to go over every letter counting up however many there are, before returning that. As a result, it’s always better to use someString.isEmpty rather than someString.count == 0 if you’re looking for an empty string.  
There are methods for checking whether a string starts with or ends with a substring: `hasPrefix()` and `hasSuffix()`.
Individual letters in strings aren’t instances of `String`, but are instead instances of `Character` – a dedicated type for holding single-letters of a string.  
One last useful method of strings is `contains()`

We want to be able to add formatting like bold or italics, select from different fonts, or add some color, and for those jobs we have a new class called `NSAttributedString`. Attributed strings are made up of two parts: a plain Swift string, plus a dictionary containing a series of attributes  

``` swift
let string = "This is a test string"
let attributes: [NSAttributedString.Key: Any] = [
    .foregroundColor: UIColor.white,
    .backgroundColor: UIColor.red,
    .font: UIFont.boldSystemFont(ofSize: 36)
]

let attributedString = NSAttributedString(string: string, attributes: attributes)

```
`UILabel`, `UITextField`, `UITextView`, `UIButton`, `UINavigationBar`, and more all support attributed strings just as well as regular strings.



#### [Day 81](https://www.hackingwithswift.com/100/81)
> remember this quote from Frank Chimero: “people ignore design that ignores people.”


[Wrap up and challenges](https://www.hackingwithswift.com/review/hws/project-24-swift-strings)

## MILESTONE: PROJECTS 22-24
#### [Day 82](https://www.hackingwithswift.com/100/82)
> Cicero once said that “to know the laws is not to memorize their letter but to grasp their full force and meaning.” 

#### [Challenge](https://www.hackingwithswift.com/guide/9/3/challenge)

1. Extend UIView so that it has a bounceOut(duration:) method that uses animation to scale its size down to 0.0001 over a specified number of seconds.
2. Extend Int with a times() method that runs a closure as many times as the number is high. For example, 5.times { print("Hello!") } will print “Hello” five times.
3. Extend Array so that it has a mutating remove(item:) method. If the item exists more than once, it should remove only the first instance it finds. Tip: you will need to add the Comparable constraint to make this work!

#### Solution

``` swift
import UIKit

// extension 1: animate out a UIView
extension UIView {
func bounceOut(duration: TimeInterval) {
    UIView.animate(withDuration: duration) { [unowned self] in
        self.transform = CGAffineTransform(scaleX: 0.0001, y: 0.0001)
        }
    }
}

// extension 2: create a times() method for integers
extension Int {
func times(_ closure: () -> Void) {
    guard self > 0 else { return }

    for _ in 0 ..< self {
        closure()
        }
    }
}    

// extension 3: remove an item from an array
extension Array where Element: Comparable {
mutating func remove(item: Element) {
    if let location = self.firstIndex(of: item) {
        self.remove(at: location)
    }
}
}

// some test code to make sure everything works
let view = UIView()
view.bounceOut(duration: 3)

5.times { print("Hello") }

var numbers = [1, 2, 3, 4, 5]
numbers.remove(item: 3)
```

## Project 25 - Selfie Share
#### [Day 83](https://www.hackingwithswift.com/100/83)
> Back in 1980, Bob Metcalfe outlined what has since become known as Metcalfe’s law: “the effect of a telecommunications network is proportional to the square of the number of connected users of the system.”

 A new technology called the multipeer connectivity framework.   
 Multipeer connectivity requires four new classes:  
 
 1. MCSession is the manager class that handles all multipeer connectivity for us.
 2. MCPeerID identifies each user uniquely in a session.
 3. MCAdvertiserAssistant is used when creating a session, telling others that we exist and handling invitations.
 4. MCBrowserViewController is used when looking for sessions, showing users who is nearby and letting them join.

``` swift
import MultipeerConnectivity

// Now add these to your view controller:

var peerID = MCPeerID(displayName: UIDevice.current.name)
var mcSession: MCSession?
var mcAdvertiserAssistant: MCAdvertiserAssistant?
```
Depending on what users select in our alert controller, we need to call one of two methods: `startHosting()` or `joinSession()`.
All multipeer services on iOS must declare a service type, which is a 15-digit string that uniquely identify your service.   
Apple's example is, "a text chat app made by ABC company could use the service type abc-txtchat"; for this project I'll be using hws-project25.

This service type is used by both `MCAdvertiserAssistant` and `MCBrowserViewController` to make sure your users only see other users of the same app. They both also want a reference to your `MCSession` instance so they can take care of connections for you.

We're going to start by initializing our `MCSession` so that we're able to make connections. Put this code into `viewDidLoad()`:

```swift
mcSession = MCSession(peer: peerID, securityIdentity: nil, encryptionPreference: .required)
mcSession?.delegate = self

// and the funcs
func startHosting(action: UIAlertAction) {
guard let mcSession = mcSession else { return }
mcAdvertiserAssistant = MCAdvertiserAssistant(serviceType: "hws-project25", discoveryInfo: nil, session: mcSession)
mcAdvertiserAssistant?.start()
}

func joinSession(action: UIAlertAction) {
guard let mcSession = mcSession else { return }
let mcBrowser = MCBrowserViewController(serviceType: "hws-project25", session: mcSession)
mcBrowser.delegate = self
present(mcBrowser, animated: true)
}
```
That's two protocols we need to conform to in order to fix our current compile failures. Easily done: add `MCSessionDelegate` and `MCBrowserViewControllerDelegate`  

When a user connects or disconnects from our session, the method `session(_:peer:didChangeState:)` is called 

``` swift
func session(_ session: MCSession, peer peerID: MCPeerID, didChange state: MCSessionState) {
    switch state {
    case .connected:
    print("Connected: \(peerID.displayName)")

    case .connecting:
    print("Connecting: \(peerID.displayName)")

    case .notConnected:
    print("Not Connected: \(peerID.displayName)")

    @unknown default:
    print("Unknown state received: \(peerID.displayName)")
    }
}
// Here's the final protocol method, to catch data being received in our session:

func session(_ session: MCSession, didReceive data: Data, fromPeer peerID: MCPeerID) {
    DispatchQueue.main.async { [weak self] in    
        if let image = UIImage(data: data) {
            self?.images.insert(image, at: 0)
            self?.collectionView.reloadData()
            }
    }
}
```

The final piece of code: 

``` swift
// 1 Check if we have an active session we can use.
guard let mcSession = mcSession else { return }

// 2 Check if there are any peers to send to.
if mcSession.connectedPeers.count > 0 {

// 3 Convert the new image to a Data object
    if let imageData = image.pngData() {

// 4 Send it to all peers, ensuring it gets delivered.
        do {
            try mcSession.send(imageData, toPeers: mcSession.connectedPeers, with: .reliable)
            } catch {

// 5 Show an error message if there's a problem
                let ac = UIAlertController(title: "Send error", message: error.localizedDescription,
                preferredStyle: .alert)
                ac.addAction(UIAlertAction(title: "OK", style: .default))
                present(ac, animated: true)
                }
            }
}
```


#### [Day 84](https://www.hackingwithswift.com/100/84)
> There are a number of well-known quotes from Steve Jobs, but if I had to pick one – my all-time favorite – it would be this: “it is in Apple’s DNA that technology alone is not enough – it’s technology married with liberal arts, married with the humanities, that yields us the results that make our heart sing.”  

[Challenge and Wrap-Up](https://www.hackingwithswift.com/review/hws/project-25-selfie-share)

## Project 26 - Marble Maze
#### [Day 85](https://www.hackingwithswift.com/100/85) 
> Dan O’Sullivan once wrote, “personal computers have evolved in an office environment in which you sit on your butt, moving only your fingers, entering and receiving information censored by your conscious mind. That is not your whole life, and probably not even the best part – we need to think about computers that sense more of your body, serve you in more places, and convey the physical expression in addition to information.”  

We're going to be using the categoryBitMask, contactTestBitMask and collisionBitMask properties in their fullest for this project, because we have very precise rules that make the game work. To clarify, here's what each of them mean:

1. The `categoryBitMask` property is a number defining the type of object this is for considering collisions.
2. The `collisionBitMask` property is a number defining what categories of object this node should collide with,
3. The `contactTestBitMask` property is a number defining which collisions we want to be notified about.


#### [Day 86](https://www.hackingwithswift.com/100/86)
> Back when the original iPad launched Apple showed off one of those “Jony Ive in an infinitely white room” videos, where Jony had this to say: “it’s true: when something exceeds your ability to understand how it works, it sort of becomes magical – and that’s exactly what the iPad is.”  

All motion detection is done with an Apple framework called Core Motion, and most of the work is done by a class called CMMotionManager. Using it here won't require any special user permissions  

```swift
var motionManager: CMMotionManager!

// Put this this into didMove(to:):

motionManager = CMMotionManager()
motionManager.startAccelerometerUpdates()
```

Special compiler instructions. `#if targetEnvironment(simulator)`, `#else` and `#endif`. 

#### [Day 87](https://www.hackingwithswift.com/100/87)
> Seth Godin – author and marketing genius – once said “surprise and delight and connection are remarkable.”

[Wrap up and review](https://www.hackingwithswift.com/review/hws/project-26-marble-maze)

## Project 27 - Custom Drawing  
#### [Day 88](https://www.hackingwithswift.com/100/88)
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


#### [Day 89](https://www.hackingwithswift.com/100/89)
> Carl Sagan once said, "if you wish to make an apple pie from scratch, you must first invent the universe."

> Swift was first introduced way back in 2014, at Apple’s annual Worldwide Developer Conference (WWDC). When showing off the new language, Chris Lattner (the creator of Swift) took to the stage and immediately did something that was revolutionary for us – at least back then: he created a Swift playground in Xcode.

- Wrap up and challenges

## MILESTONE: PROJECTS 25-27

#### [Day 90](https://www.hackingwithswift.com/100/90)
> "As John Quincy Adams once said, “patience and perseverance have a magical effect before which difficulties disappear and obstacles vanish.”

- `#targetEnvironment`(simulator) compiler directive. Swift has several of these, like `#line` and `#if swift`. 
- `#line` is easy enough: when your code gets built it automatically gets replaced with the current line number. You can also use #filename and #function, and the combination of these are very useful in debugging strings.
- The #if swift directive allows you to conditionally compile code depending on the Swift compiler version being used. So, you could write Swift 4.2 code and Swift 5.0 code in the same file, and have Xcode choose the right version automatically.

#### [Day 91](https://www.hackingwithswift.com/100/91) - CORE GRAPHICS REDUX
> Fred Donaldson : “Children learn as they play. Most importantly, in play children learn how to learn.” 

> George Bernard Shaw said, “we don’t stop playing because we grow old; we grow old because we stop playing.” 

- Playground links for [ipad](https://www.hackingwithswift.com/playgrounds) and [xcode](http://hackingwithswift.com/files/playgrounds/Learn-Core-Graphics-Xcode.zip)

## PROJECT 28 - Use the iOS keychain - Secret Swift
#### [Day 92](https://www.hackingwithswift.com/100/92)
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

#### [Day 93](https://www.hackingwithswift.com/100/93)

> As Gene Spafford once said, “the online truly secure system is one that is powered off, cast in a block of concrete and sealed in a lead-lined room with armed guards.”

- security, encryption in ios 
- If you use biometric authentication but store your data in UserDefaults, it can be read out by bypassing the app. If you store your data in the iOS keychain but don’t put it behind biometric authentication or similar, anyone can launch the app and just take it.

## PROJECT 29 - Exploding Monkeys
#### [Day 94](https://www.hackingwithswift.com/100/94) 
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


#### [Day 95](https://www.hackingwithswift.com/100/95)
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


#### [Day 96](https://www.hackingwithswift.com/100/96)
> Craig Federighi, senior vice president of software engineer at Apple, once said “people sometimes have a view of programming that is something solitary and very technical, but programming is among the most creative, expressive, and social careers.”

- wrap up

## PROJECT 29 - Instruments
#### [Day 97](https://www.hackingwithswift.com/100/97)
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

#### [Day 98](https://www.hackingwithswift.com/100/98)
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
#### [Day 99](https://www.hackingwithswift.com/100/99)
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
#### [Day 100!](https://www.hackingwithswift.com/100/100)
> As Aisha Tyler said, “success is not the absence of failure; it's the persistence through failure.”


#### Sources:  

[GitHub HackingWithSwift](https://github.com/twostraws/HackingWithSwift)  
[Talk at NSSpain Spain](http://vimeo.com/291590798)  
[HACKING WITH SWIFT ONLINE](https://www.hackingwithswift.com/read)  
[How to flip a UIView with a 3D effect: transition(with:)](https://www.hackingwithswift.com/example-code/uikit/how-to-flip-a-uiview-with-a-3d-effect-transitionwith)  
