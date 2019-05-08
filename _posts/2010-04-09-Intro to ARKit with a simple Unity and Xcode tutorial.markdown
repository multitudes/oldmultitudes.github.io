---
layout: post
title:  "Intro to ARKit with a simple Unity and Xcode tutorial"
date:   2010-04-09
categories: iOS, developer
comments: true
published: true
---


<div class="message">
"For the world to be interesting, you have to be manipulating it all the time" 
<br><cite>Brian Eno</cite>
</div>

![image](/assets/img/louis-maniquet-684906-unsplash.jpg)
<cite>Photo by Louis Maniquet on Unsplash</cite>
<br>
### Intro - What is ARKit.
ARKit is the Augmented Reality Framework for Apple devices which enables developers to create Augmented Reality Apps for iPhone & iPad. It was introduced along with iOS 11 during WWDC 2017. 
Anyone using an iOS device that runs on Apple's A9 to A12 Bionic processors (& running iOS 11 or above) can use ARKit apps.
ARKit apps put three-dimensional images in your world using what's called visual inertial odometry
It’s the Apple alternative to Google Project Tango but puts fewer demands on the hardware. Project Tango required a special camera array with dual cameras and an IR transmitter to get a rough 3D model of a room on the fly.
ARKit doesn’t require this. Instead, it recognises planes, like your floor. Then it uses the iPhone’s camera and its motion detectors to track the movement as the iPhone is moved and tilted.
ARKit may not be able to judge the layout of a room with a single, perfectly still view of a scene. But it can instantly re-analyse that same scene when your hand movements cause the phone to tilt by a few degrees.
This communication between the motion sensors and the camera makes it possible to get a fairly accurate 3D representation of the surroundings.


### ARKit 2.0 image tracking feature

The current version is ARKit 2.0 and a new version of ARKit should be out soon, at WWDC 2019 at the latest.

In this tutorial, we are going to build a simple AR app in Unity using ARKit 2.0 image tracking feature

We will need:

- iOS 12 or later on our device
- Xcode 10 or later on our Mac

### Create your first ARKit application.

To create AR apps there are 3 main frameworks to choose from:

– The Unity Engine 
- The Unreal Engine
- Xcode

In this tutorial I will show how to create an simple AR application for your iPhone or iPad in Unity and Xcode. For this you would need a picture both in digital format and printed (to be recognized by your iOS device). And three small mp4 videos in size of max 24Mb. 

#### Install ARKit 2.0

ARKit is a framework so it needs to be imported into a Unity to create AR apps. 

Go to this link, download the [ARKit 2.0 installer](https://bitbucket.org/Unity-Technologies/unity-arkit-plugin/downloads/) and open it in Unity.


![image](/assets/img/ARKittutorialscreenshots/13.32.57.png)

the image detection feature was introduced in ARKit 1.5
but with the image detection, you can just scan the image target and trigger an AR
experience but you would not track that image. 
Now in ARkit 2.0, you can track the position of image targets as well.
If you move the image target any overlay that you have on that image target, whether it's a model or a video, will move along with the image.

Let's open the unzipped downloaded folder with Unity Hub. I am using Unity 2018.3.11
Screen Shot 2019-05-07 at 13.58.25.png
Screen Shot 2019-05-07 at 13.58.41.png
Open the folder UnityARKitPlugin and the Examples folder. In the screenshots, your Unity might look different. Look for the assets folder in your Project Tab.

Open the folder ARKit1.5 and the UnityARImageAnchor

Drag the image you want to use as an image-trigger in the ReferenceImages folder:
Screen Shot 2019-05-07 at 14.05.40.png
Now go up once in the Folder Hierarchy and click on UnityLogoReferenceImage which is part of the Unity demo. We gonna change the trigger image. 
Screen Shot 2019-05-07 at 14.10.02.png
Drag and drop your image from the ReferenceImages folder to the Image Texture field in the Inspector.
Screen Shot 2019-05-07 at 14.10.09.png
In my case, the image is called earth.
Screen Shot 2019-05-07 at 14.12.49.png
Right-click in the hierarchy and select “Create Empty”. You get a Game  Object folder. Rename it to “parent”.
Screen Shot 2019-05-07 at 14.14.21.png
Right-click again in the Hierarchy tab and select 3D object and Plane
Screen Shot 2019-05-07 at 14.16.13.png
Looks like this
Screen Shot 2019-05-07 at 14.17.01.png
Reset the position for Plane and parent to 0
Screen Shot 2019-05-07 at 14.17.54.png
Measure the actual real dimension of your image an input it in the scale property
Remember they are in meter, so the x will be ex 0.0109 and the z 0.006138
Screen Shot 2019-05-07 at 14.20.32.png
In the ReferenceImages folder right click and create a material for the card and name it image
Screen Shot 2019-05-07 at 14.25.55.png
In the inspector go to legacy shader/ diffuse
Screen Shot 2019-05-07 at 14.28.05.png
Click in the right square texture.. select the image from the popup window
Screen Shot 2019-05-07 at 14.30.49.png
And from the scroll down UI/ default
Screen Shot 2019-05-07 at 14.32.07.png

Now drag the material called image to the image in the hierarchy.
Screen Shot 2019-05-07 at 14.32.51.png

This is how it looks like for me. You can rotate or change things in the inspector if you need...
Screen Shot 2019-05-07 at 14.34.33.png

Drag the image inside the parent
Screen Shot 2019-05-07 at 14.45.06

And duplicate this. It is command-D on the Mac to duplicate.
They will be one on top of the other so click in the Scene and drag them to where you need them.
Screen Shot 2019-05-07 at 14.47.23.png

It will look like this now
Screen Shot 2019-05-07 at 14.50.14.png

The first will be our trigger image

And then there would be the three videos which will play and
move along with the image.
Let's attach three videos to these three new planes.
Rename them as "1", "2", "3" for instance. 
Screen Shot 2019-05-07 at 14.54.08.png
and drag the three videos to the ReferenceImages folder.
And then one by one from the folder to the three just creates planes 1,2, and 3

If you click play you should see the three videos playing

Now drag the parent folder from the hierarchy to the assets and automatically a prefab will be created



let's run the project
go to file build settings, switch to the
iOS platform and then click on add open scenes. Now build and save.
This will create an Xcode build.
Open it in Xcode. Go to images in the assets folder.
resources and click on your image.
Change the size to cm and the dimension of our physical image.
Select your team in General, and make sure that the deployment target is 12.0  
Choose the device and rn the app.


### sources
About ARKit 11 - 26 July 2017
https://www.theverge.com/tldr/2017/7/26/16035376/arkit-augmented-reality-a-ha-take-on-me-video-trixi-studios

Use of ARKit
https://twitter.com/jaromvogel/status/1125401258494324736

I’ve seen a bunch of ARKit demos that made me think “That’s very cool”. This was the first one that made me think “That’s very useful”

https://twitter.com/madewitharkit


#### Apps

The Ikea App has been one of the first demos for ARKit 
gaming will be another big market

The App Store offers a curated section to highlight the best AR experiences. Just tap on Apps and scroll down to Top Categories. AR Apps is at the top.

This is the official app page for developer
https://developer.apple.com/arkit/

<hr>
