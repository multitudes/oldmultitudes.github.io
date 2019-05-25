---
layout: post
title:  "Integrating Apps and Content with AR Quick Look"
date:   2010-04-09
categories: iOS, developer
comments: true
published: true
---


<div class="message">
"With iOS 12, ARKit includes a built-in viewer for displaying and sharing high-quality 3D content using Pixar's usdz file format. " 
<br><cite>Apple Developer Website - Keynote WWDC 2018</cite>
</div>

![image](/assets/img/CSharpScriptingPost.jpg)

### 

ARKit, Apple's augmented reality (AR) technology, delivers immersive, engaging experiences that seamlessly blend virtual objects with the real world. In AR apps, the device's camera presents a live, onscreen view of the physical world. Three-dimensional virtual objects are superimposed over this view, creating the illusion that they actually exist. The user can reorient their device to explore the objects from different angles and, if appropriate for the experience, interact with objects using gestures and movement.

AR is becoming the tool to see what objects look like in the world.  
Really easy to integrate.  
AR Quick Look was designed to enrich any application on the OS with AR content with a simpler way to adopt AR previewing for consistent viewing experience.

 AR Quick Look is built in and deeply integrated into the OS to allow previewing from any application and websites, it is available in iOS 12 on ARKit compatible devices and only object mode on non-ARKit supported devices. AR Quick Look handles setting up the AR experience like plane detection, object placement, gesture manipulations, and creating contact shadows.

It's really easy to adopt and integrate the viewer into a website and application and it could be as simple as embedding a usdz file if your application already supports and uses Quick Look.

For a demo go to the [AR Gallery](https://developer.apple.com/arkit/gallery/) and look for thumbnails with the AR badge stamp at the top right-hand corner, and that's there to tell you that there's an AR experience behind this.  

 So, you can really pan around and see the model from various different angles.
 We can pinch to size an object and make it look a lot larger and really see the fine details that went into this model.  
 
And just like a photo, you can double tap on the model to recess the position and the size.  
We're matching the color intensity and the temperature that's reported by ARKit from the world, and we're using that with our lighting setup.  

#### Accessibility

##### VoiceOver

Now you get audible feedback for when my Model is off screen and back on screen.

#### Integration in First Part Apps  

AR Quick Look integrated into the files app, but that's one of six first party apps to have adopted and integrate the viewer.  

The others are mail, messages, notes, news, and Safari.




### Human Interface Guidelines

From the [Apple Developer pages:](https://developer.apple.com/design/human-interface-guidelines/ios/system-capabilities/augmented-reality/)

- Use the entire display. Avoid cluttering the screen with controls and information that diminish the immersive experience.  
- Create convincing illusions when placing realistic objects.design detailed 3D assets with lifelike textures. Use the information ARKit provides to position objects on detected real-world surfaces, scale objects properly, reflect environmental lighting conditions on virtual objects, cast top-down diffuse object shadows on real-world surfaces, and update visuals as the camera's position changes. Make sure your app updates the scene 60 times per second so objects don’t appear to jump or flicker.  
- Consider how virtual objects with reflective surfaces show the environment.  
- Anticipate that people will use your app in environments that aren’t optimal for AR. People may open your app in a location where there isn't much room to move around or there aren't large, flat surface areas.  
- Be mindful of the user's comfort. Holding a device at a certain distance or angle for a prolonged period can be fatiguing. 
- Favor indirect controls that enable one-handed use of your app. Controls in screen space are easier to target and less likely to require users to adjust how they’re holding their device. Make controls large enough to easily and accurately target with one finger and use translucency to occlude as little of the underlying scene as possible.  
- If your app encourages user motion, introduce it gradually.  
- Be mindful of the user's safety.
- Use audio and haptic feedback to enhance the immersive experience.   
- Wherever possible, provide hints in context. Placing a three-dimensional rotation indicator around an object, for example, is more intuitive than presenting text-based instructions in an overlay.  
- Consider guiding people toward offscreen virtual objects.  
- If you must display instructional text, use approachable terminology.   
- Make important text readable. Display text used for labels, annotations, and instructions as if it is attached to the phone screen rather than in the virtual space. The text should face the user and be shown at the same size regardless of the distance of the labeled object.  
- Consider displaying additional information in screen space.
- Indicate when initialization and surface detection is in progress and involve the user.  







{% highlight csharp %}

{% endhighlight %}




### Sources:


<hr>
