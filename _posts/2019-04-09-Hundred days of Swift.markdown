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
#### Day 39
> Joss Whedon, the creator of Firefly, once said that “the secret to multitasking is that it isn't actually multitasking – it’s just extreme focus and organization.” (If you weren’t aware, Firefly played a big part in the development of Swift – the internal code name (“Shiny”) was from there


#### Day 40
#### Day 41
#### Day 42
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

## PROJECT 28
#### Day 92
> Fred Donaldson : “Children learn as they play. Most importantly, in play children learn how to learn.” 

> George Bernard Shaw said, “we don’t stop playing because we grow old; we grow old because we stop playing.” 
#### Day 93
#### Day 94
#### Day 95
#### Day 96
#### Day 97
#### Day 98
#### Day 99

#### Day 100!


PROJECT 27
#### Sources:

[GitHub HackingWithSwift](https://github.com/twostraws/HackingWithSwift)
[Talk at NSSpain Spain](http://vimeo.com/291590798)