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
The only thing I am missing is sometimes when I am looking for old content. There is no index on the website and after a certain number of projects under your belt you feel the need to revisit some of the staff. Where was that petition API again ? 

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

``` Swift
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
``` Swift
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
``` swift
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

- pixels and points - retina screens - file@2x.png | file@3x.png
- `button1.setImage(UIImage(named: countries[1]), for: .normal) `
- UIButton and CALayer - CGColor:  `button1.layer.borderColor = UIColor.lightGray.cgColor`

#### Day 20

> Steve Jobs said, "I believe life is an intelligent thing: that things aren't random.” 
- shuffled() to return a new, shuffled array. shuffle() for in-place shuffling
- Int.random(in: 0...2)
- @IBAction func buttonTapped(_ sender: UIButton) {}
- Tag - `sender.tag`
- UIAlertController()
``` swift
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

``` swift
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

##  Project 4 - Simple web browser
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
- `webView.addObserver(self, forKeyPath: #keyPath(WKWebView.estimatedProgress), options: .new, context: nil)`


<hr>
<hr>
<hr>





#### Sources:

[GitHub HackingWithSwift](https://github.com/twostraws/HackingWithSwift)
