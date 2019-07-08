---
layout: post
title:  "Introducing ARKit3"
date:   2019-06-23
categories: iOS, developer
comments: true
published: true
---

This is an extract of the Apple Developer Keynote's talk [Introducing ARKit3](https://developer.apple.com/videos/play/wwdc2019/604/)
for my own enjoyment and learning 

![image](/assets/img/arkit3/1.png)

This is the third major release of ARKit which has been introduced in 2017.  
ARKit provides three pillars of functionalities.

- Tracking  

It determines where your device is respect to the environment, so that virtual content can be positioned and updated correctly in real time.  
This creates the illusion that the virtual content is placed in the real world.  
ARKit provides different tracking technologies such as worldtracking, facetracking and imagetracking.

-Scene understanding  

This sits on top of tracking and with it you can identify surfaces, images and 3D Objects in the sceneand attach virtual content right on them.  
Also learns about the lighting and texture to help make the content more realistic.

- Rendering

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



## Sources  

[WWDC Talk - Introducing ARKit3](https://developer.apple.com/videos/play/wwdc2019/604/)  

[https://developer.apple.com/augmented-reality/quick-look/](https://developer.apple.com/augmented-reality/quick-look/)  

[Download usdz tools](https://developer.apple.com/go/?id=python-usd-library)  
<br>
