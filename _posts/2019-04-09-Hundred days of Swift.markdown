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

## [Day 1-12](https://www.hackingwithswift.com/100/1)  - Introduction to Swift   

All what you need to know about optionals and closures etc.  
See my other post with more details [here](https://multitudes.github.io/2019/04/Some-Swift-tips-for-beginner-and-intermediate.html).

<hr>

## [Day 13-14-15](https://www.hackingwithswift.com/100/13)  - Consolidation and review

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
#### [Day 17](https://www.hackingwithswift.com/100/17)  

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

#### [Day 18](https://www.hackingwithswift.com/100/18) 

- Wrap up

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

## 
#### [Day 62](https://www.hackingwithswift.com/100/62)
#### [Day 63](https://www.hackingwithswift.com/100/63)
#### [Day 64](https://www.hackingwithswift.com/100/64)
#### [Day 65](https://www.hackingwithswift.com/100/65)
#### [Day 66](https://www.hackingwithswift.com/100/66)
#### [Day 67](https://www.hackingwithswift.com/100/67)
#### [Day 68](https://www.hackingwithswift.com/100/68)
#### [Day 69](https://www.hackingwithswift.com/100/69)
#### [Day 70](https://www.hackingwithswift.com/100/70)
#### [Day 71](https://www.hackingwithswift.com/100/71)
#### [Day 72](https://www.hackingwithswift.com/100/72)
#### [Day 73](https://www.hackingwithswift.com/100/73)
#### [Day 74](https://www.hackingwithswift.com/100/74)
#### [Day 75](https://www.hackingwithswift.com/100/75)
#### [Day 76](https://www.hackingwithswift.com/100/76)
#### [Day 77](https://www.hackingwithswift.com/100/77)
#### [Day 78](https://www.hackingwithswift.com/100/78)
#### [Day 79](https://www.hackingwithswift.com/100/79)
#### [Day 80](https://www.hackingwithswift.com/100/80)
#### [Day 81](https://www.hackingwithswift.com/100/81)
#### [Day 82](https://www.hackingwithswift.com/100/82)
#### [Day 83](https://www.hackingwithswift.com/100/83)
#### [Day 84](https://www.hackingwithswift.com/100/84)
#### [Day 85](https://www.hackingwithswift.com/100/85)
#### [Day 86](https://www.hackingwithswift.com/100/86)
#### [Day 87](https://www.hackingwithswift.com/100/87)

## Project 27 - custom drawing  
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


PROJECT 27
#### Sources:

[GitHub HackingWithSwift](https://github.com/twostraws/HackingWithSwift)
[Talk at NSSpain Spain](http://vimeo.com/291590798)
[HACKING WITH SWIFT ONLINE](https://www.hackingwithswift.com/read)
[How to flip a UIView with a 3D effect: transition(with:)](https://www.hackingwithswift.com/example-code/uikit/how-to-flip-a-uiview-with-a-3d-effect-transitionwith)
