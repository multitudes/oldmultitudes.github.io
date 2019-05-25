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

![image](/assets/img/AR-QL-Pictures/Screenshot1.png)

### ARKit 

ARKit, Apple's augmented reality (AR) technology, delivers immersive, engaging experiences that seamlessly blend virtual objects with the real world. In AR apps, the device's camera presents a live, onscreen view of the physical world. Three-dimensional virtual objects are superimposed over this view, creating the illusion that they actually exist. The user can reorient their device to explore the objects from different angles and, if appropriate for the experience, interact with objects using gestures and movement.

AR is becoming the tool to see what objects look like in the world. And it is really easy to integrate. AR Quick Look is built in and deeply integrated into the OS to allow previewing from any application and websites, it is available in iOS 12 on ARKit compatible devices and only object mode on non-ARKit supported devices. AR Quick Look handles setting up the AR experience like plane detection, object placement, gesture manipulations, and creating contact shadows.  

It's really easy to adopt and integrate the viewer into a website and application and it could be as simple as embedding a usdz file if your application already supports and uses Quick Look.

AR Quick Look was designed to enrich any application on the OS with AR content with a simpler way to adopt AR previewing for consistent viewing experience.

For a demo go to the [AR Gallery](https://developer.apple.com/arkit/gallery/) and look for thumbnails with the AR badge stamp at the top right-hand corner, and that's there to tell you that there's an AR experience behind this.  


So, you can really pan around and see the model from various different angles.
We can pinch to size an object and make it look a lot larger and really see the fine details that went into this model.  
 
And just like a photo, you can double tap on the model to recess the position and the size.  
We're matching the color intensity and the temperature that's reported by ARKit from the world, and we're using that with our lighting setup.  

#### Accessibility - VoiceOver

Now you get audible feedback for when my Model is off screen and back on screen.

#### Integration in First Part Apps  

AR Quick Look is integrated into the files app, mail, messages, notes, news, and Safari.

![image](/assets/img/AR-QL-Pictures/Screenshot2.jpg)

#### Quick Look

#### USDZ

![image](/assets/img/AR-QL-Pictures/ARKit-Badge.pdf)

Sharing a 3D model between all these apps requires the models to be bundled up in a single sharable file.  

To enable this, AR Quick Look supports `usdz`, which is a new file format for mobile distribution of 3D models.  
`usdz` packages all these models and textures into a single file for efficient delivery of 3D content without having to work with reference files.  
It's based on Pixar's open-source `Universal Scene Description` format, or short, `USD`.  

You can integrate AR Quick Look in two different mediums, in an application or in websites in Safari.  

##### Quick Look API

Let's get started with applications and how the Quick Look API is used to provide an AR experience.  
Quick Look about previewing documents like Keynotes, PDFs, images, and now 3D model files like usdz.  
Security is handled for you where the contents of the usdz file is safely read to present a preview for you.  

Lets see the code:

We have a `ViewController` with a grid of thumbnails for various 3D models.  
When someone taps on one of these thumbnails, I want to show a Quick Look preview of the model for that thumbnail.  

With all that configured, we're ready to present our preview controller, and so it's going to animate and scale up from the view that was tapped.  
In order to preview and present documents, we need to instantiate a QLPreviewController.  
It's part of the Quick Look framework.  
Let's take a look at the protocol for a dataSource.  

I create a `QLPreviewController`.

{% highlight swift %}

func preview(_ sender: Any) {
    let previewController = QLPreviewController() 
    previewController.dataSource = self
    previewController.delegate = self
    // Present viewer modally
    present(previewController, animated: true, completion: nil)
}

func numberOfPreviewItems(in controller: QLPreviewController) -> Int { 
    // Viewer supports previewing a single 3D object
    return 1 
}
 
func previewController(
_ controller: QLPreviewController, previewItemAt index: Int) -> QLPreviewItem {
    // Return the file URL to the .usdz file
    let fileUrl = Bundle.main.url(forResource: “radar_aardvark”, withExtension: “usdz”)! 
    return fileUrl as QLPreviewItem
}
{% endhighlight %}

AR Quick Look is intended to be presented full screen.

{% highlight swift %}

func previewController(_ controller: QLPreviewController, transitionViewFor item: QLPreviewItem) -> UIView? {
// Provide the starting view for a seamless zoom transition to the viewer
return self.startingZoomView
}

{% endhighlight %}

And for an overall better experience, I recommend using a UI button as the view and setting the thumbnail as the button's image.  
That way, you get visual feedback whenever the view is tapped with the button highlight, and this is extremely important so that the user knows that some action is about to happen.  
If possible, I suggest the final or UIView to have a square frame, to have the best seamless transition.  
AR Quick Look nicely handles the transition from this view to the full screen viewer on presentation and dismissal, creating this effect where the model just magically appears.  

##### In Safari

Starting in iOS 12, Safari has built-in support for previewing usdz files in AR.  
By hosting usdz files on your website, you got a way of delivering previews of 3D objects.  

For better integration of AR on my web content, I'll use the new HTML markup:
By following this markup, you have badge rendered on the image in the top right-hand corner, and this is useful and there to tell you that our system viewer can preview my object in AR.  

The requirement is an a elements with rel=ar, and this tells WebKit that this is AR content.  
You then provide the link to the location of the usdz file.  

{% highlight html %}

<a rel="ar" href="model.usdz">
    <img src="model-preview.jpg">
</a>

{% endhighlight %}

Or working with the picture element:


{% highlight html %}
 
<a rel="ar" href="model.usdz">
    <picture>
        <source srcset=“wide-image.png”
            media="(min-width: 600px)"> <img src="narrow-image.png">
    </picture>
</a>

{% endhighlight %}

`usdz` content must be served with the correct media type, and so make sure that the `MIME` type is set for these files.[^1]  

`AddType model/vnd.pixar.usd .usdz`  
`AddType model/usd usdz`  



#### How to convert 3D models into the usdz format using the new usdz Converter tool in Xcode 10.

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










### Notes


[^1]: What are MIME types?
MIME types describe the media type of content either in email or served by web servers or web applications and are intended to help guide a web browser in how the content is to be processed and displayed. Examples of MIME types are:  
- text/html for normal web pages  
- text/plain for plain text  
- text/css for Cascading Style Sheets  
- text/javascript for scripts
To define a new MIME type you should add the following line in a file named `.htaccess` in the folder where the files for your website reside:
ex: `AddType TYPE .extension`

### Sources:

https://developer.apple.com/videos/play/wwdc2018/603/

https://forums.developer.apple.com/thread/104042

https://developer.apple.com/videos/play/wwdc2018/237/

<hr>
