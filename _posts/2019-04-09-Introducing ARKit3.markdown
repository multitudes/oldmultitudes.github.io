---
layout: post
title:  "Introducing ARKit3"
date:   2019-07-06
categories: iOS, developer
comments: true
published: true
---

This is an extract of the Apple Developer Keynote's talk [Introducing ARKit3](https://developer.apple.com/videos/play/wwdc2019/604/)
for my own enjoyment and learning 

![image](/assets/img/arkit3/1.png)

ARKit provides three pillars of functionalities.

### Tracking  

It determines where your device is respect to the environment, so that virtual content can be positioned and updated correctly in real time.  
This creates the illusion that the virtual content is placed in the real world.  
ARKit provides different tracking technologies such as worldtracking, facetracking and imagetracking.

### Scene understanding  

This sits on top of tracking and with it you can identify surfaces, images and 3D Objects in the sceneand attach virtual content right on them.  
Also learns about the lighting and texture to help make the content more realistic.

### Rendering

Brings the 3D content to life.  
There are three main renderers: SceneKit, SpriteKit, Metal ...  

![image](/assets/img/arkit3/2.png)

and from this year Reality Kit, designed for AR.  

![image](/assets/img/arkit3/3.png)

## New Features in ARKit3

Some of them are Visual Coherence, Positional Tracking, Simultaneous Front and Back Camera, Record and Replay of Sequences, More Robust 3D Object Detection, Multiple-face Tracking, HDR Environment Textures, Faster Reference Image Loading, Motion Capture, Detect up to 100 Images, Face Tracking Enhancements, People Occlusion, Raycasting, Collaborative Session, ML Based Plane Detection, New Plane Classes, RealityKit Integration, AR Coaching UI.

### People Occlusion 

![image](/assets/img/arkit3/4.png)

(Available on A12 and later)  

Enables virtual content to be rendered behind people and works for multiple people in the scene, for fully and partially visible people and integrates with ARView and ARSCNView.  

To produce a convincing AR experience is important to position the content accurately and also to match the world lighting.  
When people are in the frame it can quickly break the illusion because when they are in the front, they are expected to cover the model. With people occlusion this problem is solved.  
Virtual content by default is rendered on top of the camera image. Thanks to machine learning it recognize people placed in the frame and then creates a separate layer including only the pixel representing the people. We call this segmentation. Then we can render that layer on top of everything else. But this would not enough. ARKit uses machine learning to make an additional depth estimation test to understand how far the segmented people are in regard to the camera and to make sure to render only people up front if they are actually closer to the camera. Thanks to the power of the Neural Engine in the A12 chip we are able to do it in every frame in real time.  


![image](/assets/img/arkit3/5.png)

Let's see it in code:  
We have a new property on ARConfiguration called FrameSemantics.  

This will give you different semantic information of what is in the current frame.  

``` swift

class ARConfiguration : NSObject {
   var frameSemantics: ARConfiguration.FrameSemantics { get set }
   class func supportsFrameSemantics(ARConfiguration.FrameSemantics) -> Bool
}
```

Specific for People Occlusion there are two methods available:   
One option is personSegmentation.  
This is the best when you know people will be always be in the front.   

``` swift

let configuration = ARWorldTrackingConfiguration() 
configuration.frameSemantics = .personSegmentation
session.run(configuration)

```

The other option is person segmentation with depth.  
This is best if people will be either behind or in the front   

``` swift

let configuration = ARWorldTrackingConfiguration() 
configuration.frameSemantics = .personSegmentationWithDepth
session.run(configuration)

```
For advanced user using Metal you can access the data of the segmentation on every frame like this:  

``` swift

open class ARFrame : NSObject, NSCopying {
    open var segmentationBuffer: CVPixelBuffer? { get } 
    open var estimatedDepthData: CVPixelBuffer? { get }
}

```

Let's see an example of using the API.   
In `viewDidLoad` you create an anchor entity looking for horizontal planes and adding it to a scene.  
Then you retrieve the `url` of the model to load and load it using loadModelAsync in asynchronous model.  
We add the entity as a child of our anchor and also add support for gestures.   
This will automatically set up a WorldTracking configuration thanks to realityKit.

![image](/assets/img/arkit3/6.png)

I want to implement a toggle that switches occlusion on and off with a simple tap.  
We need always to check if the device supports FrameSemantic and gracefully handle that case.  

![image](/assets/img/arkit3/7.png)

And add the toggle function   
![image](/assets/img/arkit3/8.png)

## Motion Capture

(Available on A12 and later)
Tracks human body in 2D and 3D.  
You can track the body of a person and skeleton representation which can then be mapped to a virtual character in real time.
This is made possible by advanced Machine Learning algorythms

### 2D Body Detection
We have a new framesemntics option called .bodyDetection 
This is supported on the WorldTrackingConfiguration and on the Image and Orientation tracking configuration

``` swift
let configuration = ARWorldTrackingConfiguration() 
configuration.frameSemantics = .bodyDetection
session.run(configuration)
```
let's have a look at the data you will getting back.

Every ARFrame delivers an object of type ARBody2D in the dectected body property if a erson was detected.
This object contains a 2D Skeleton ARSkeleton2D and it will provide you with all the joints landmarks in normalized image space.
They are been returned in a flat hierarvhy in an array because this is more efficient for processing, but you also will be getting a skeleton definition and there you have all the information about how to interpret the skeleton data.  
In particular it contains information about the hierarchy of joints. Like the fact that the hand joint is a child of the elbow joint.

### 3D Motion capture

Tracks a human body pose in 3D space and provides a 3D skeleton representation with scale estimation to let you determine the size of the person that is being tracked and it is anchored in world coordinates.
We are introducing a new configuration called ARBodyTrackingConfiguration.
The frame semantics is turned on by default in that configuration. In addition it trackes device position and orientation and selected worldtrcking features such as plane estimation or image detection.
In code:
``` swift
if ARBodyTrackingConfiguration.isSupported {
   let configuration = ARBodyTrackingConfiguration()
session.run(configuration) }
```
When ARKit is running and detects a person it will detect a new type of anchor, an ARBodyAnchor. This will provided in the session anchor call back like other anchor types you know. It also has a transform with the position and orientation of the detected person in Worldcoordinates, in addition you get the scale factor and a reference to the 3d skeleton:
``` swift
open class ARBodyAnchor : ARAnchor {
    open var transform: simd_float4x4 { get } 
    open var estimatedScaleFactor: Float { get } 
    open var skeleton: ARSkeleton3D { get }
}
```
The yellow joints are the ones which will be delivered to the users with motion capture data. 
The white ones are leaf joints, additionally available in the skeleton but these are not actively tracked. Labels are available and in the API you can query them by their particular name.

One particular use case is animate a 3d character
### Animating 3D Characters

You will need a rigged mesh. To do this in code with a realityKit API.
First you create an anchor entity of type body and add this anchor to the scene (1)
Then load the model (2) and use the asynchronous loading API for that and in the completion handler you will be getting the boidy tracked entity that you just need to add to add as a child to our body anchor.
In this way the pose of the keleton will be applied to the model in real time

``` swift
// Animating a 3D character with RealityKit

    // Add body anchor (1)
    let bodyAnchor = AnchorEntity(.body)
    arView.scene.addAnchor(bodyAnchor)
    
    // Load rigged mesh (2)
    Entity.loadBodyTrackedAsync(named: "robot").sink(receiveValue: { (character) in
        
        // Assign body anchor
        bodyAnchor.addChild(character)
 })

```

### Simultaneous Front and Back Camera


Enables World Tracking with face data
Enables Face Tracking with device orientation and position Supported on A12 and later

ARKit lets you do Worldtracking on the back facing camera and face tracking with the true depth system on the front.
You can build AR experiences using front and back camera at the same time. And face tracking experiences that make use of the device orientation and position.
All this is supported on A12 and later.
Example. We run world tracking with plane estimation and also we placed a face mesh on top of the plane and updating it in real time with facial expressions captured through the front camera.

Lets see the api
First we create a world tracking configuration. This will determines which camera stream will be displayed on the screen. This will be the backfacing camera.
Now I am turning on the new face tracking enabled property and run the session.
This will cause to receive face anchors and I can use any information from that anchor like face mesh and anchor transform etc.  
Since we are working with world coordinates the user face transform will be placed behind the camera, so in order to visualize the face you will need to transform to a location somewhere in front of the camera.


``` swift
// Enable face tracking in world tracking configuration
let configuration = ARWorldTrackingConfiguration()
if configuration.supportsUserFaceTracking {
}
configuration.userFaceTrackingEnabled = true
session.run(configuration)

// Receive face data
func session(_ session: ARSession, didAdd anchors: [ARAnchor]) {
for anchor in anchors where anchor is ARFaceAnchor {
}
...
}
```

Lets see the face tracking configuration. You create the configuration as always and set the worldTrackingEnabled to true. And then you can access in every frame, call back the transform of the current camera position and you can use this for whatever use case you have in mind.


``` swift
/ Enable world tracking in face tracking configuration
let configuration = ARFaceTrackingConfiguration()
if configuration.supportsWorldTracking {
}
configuration.worldTrackingEnabled = true
session.run(configuration)

// Access world position and orientation
func session(_ session: ARSession, didUpdate frame: ARFrame) {
let transform = frame.camera.transform
...
}
```

## Collaborative Session
Before in ARKit two you were able to create multiuser experiences but you had to save the map on one device and send it to another one in order for your user to jump to the same experience.
Now with collaborative Session in ARKit 3 you are continuosly sharing the mapping information between multiple devices across the network. This allows to create Ad-hoc multi-user experiences and additionally to share ARAnchors on all devices. All those anchors are identifiable with sessions ID's on all devices
At this point all coordinate systems are indipendent from each others even we share the information under the hood.

In this example two user gather and share feature points in the world space. The two maps merge into each other and will form one map only. Additionally the other user will be shown as ArParticipantAnchor too which will allows you to detect when another user is in your environment. It is not limited to two user but you can have a large amount of users in one session.

//pic
To start in code:

``` swift
// Enable a collaborative session with RealityKit
 // Set up networking
    setupMultipeerConnectivity()
 // Initialize synchronization service
    arView.scene.synchronizationService =
    try? MultipeerConnectivityService(session: mcSession)
// Create configuration and enable the collaboration mode
    let configuration = ARWorldTrackingConfiguration()
    configuration.isCollaborationEnabled = true
    arView.session.run(configuration)

```

When the collaboration is enabled you will be have a new method on the delegate for you where you will be receiving some data. Upon receiving that data you need to broadcast on the network to other user. Upon reception of the data on all the devices you need to update the AR session so that it knows about the new data.  

``` swift
// Session callback when some collaboration data is available
override func session(_ session: ARSession, didOutputCollaborationData data:
ARSession.CollaborationData) {
    // Send collaboration data to other participants
    mcSession.send(data, toPeers: participantIds, with: .reliable)
}
// Multipeer Connectivity session delegate callback upon receiving data from peers
func session(_ session: MCSession, didReceive data: Data, fromPeer peerID: MCPeerID) {
    // Update the session with collaboration data received from another participant
    let collaborationData = ARSession.CollaborationData(data)
    session.update(from: collaborationData)
}
```




## Sources  

[WWDC Talk - Introducing ARKit3](https://developer.apple.com/videos/play/wwdc2019/604/)  

[https://developer.apple.com/augmented-reality/quick-look/](https://developer.apple.com/augmented-reality/quick-look/)  

[Download usdz tools](https://developer.apple.com/go/?id=python-usd-library)  
<br>
