---
layout: post
title:  "Augmented reality app in 150 lines of code on iOS with Swift"
date:   2010-01-22
categories: iOS, developer, augmented reality
comments: true
published: true
---


<div class="message">

<br><cite></cite>
</div>

 
 You will need a physical device to try out the code in the application, with a processor A9 or higher like an iPhone 6s.  
 
 Open a new Xcode project and choose "Augmented Reality App", content technology : `SceneKit`.  
 
 You can publish the project to GitHub if you like checking the box and then command-2 and right click and choose `Create ... Remote`  
 
 Delete the folder `art.scnassets`  
 
 In `ViewController.swift` get rid of statistics, scene,  the empty delegate methods.   
 
 It will look like this  
 
 ``` swift
 import UIKit
 import SceneKit
 import ARKit
 
 class ViewController: UIViewController, ARSCNViewDelegate {
 
 @IBOutlet var sceneView: ARSCNView!
 
 override func viewDidLoad() {
 super.viewDidLoad()
 
 // Set the view's delegate
 sceneView.delegate = self
 
 }
 
 override func viewWillAppear(_ animated: Bool) {
 super.viewWillAppear(animated)
 
 // Create a session configuration
 let configuration = ARWorldTrackingConfiguration()
 
 // Run the view's session
 sceneView.session.run(configuration)
 }
 
 override func viewWillDisappear(_ animated: Bool) {
 super.viewWillDisappear(animated)
 
 // Pause the view's session
 sceneView.session.pause()
 }
 
 }
 
 ```
 
 At this stage you have the basic scaffolding for the App.
 You can download it from GitHub if you prefer or make a branch.
 
 ## Let's start
 
 Right click in the asset catalog and select `add resorce group`  
 
 Add your tracking pictures in the folder.  
 
 in `ViewController.swift` change `let configuration = ARWorldTrackingConfiguration()` to ` let configuration = ARImageTrackingConfiguration()`
 
 Type `nodefor` and the methot will autocomplete:
 ```swift
 
 func renderer(_ renderer: SCNSceneRenderer, nodeFor anchor: ARAnchor) -> SCNNode? {
 <#code#>
 }
 
 ```
 
 
 
 
#### Sources:

[Building an ARKit app with SceneKit and Codable – Swift on Sundays April 28th 2019](https://youtu.be/XqRVfB521Fo)
[](https://developer.apple.com/documentation/spritekit/skvideonode/adding_a_video_to_a_scene)
