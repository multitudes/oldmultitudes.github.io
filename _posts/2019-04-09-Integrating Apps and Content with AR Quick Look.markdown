---
layout: post
title:  "ARKit - Integrating Apps and Content with AR Quick Look"
date:   2018-05-23
categories: iOS, developer
comments: true
published: true
---


<div class="message">
"With iOS 12, ARKit includes a built-in viewer for displaying and sharing high-quality 3D content using Pixar's usdz file format. " 
<br><cite>Apple Developer Website - Keynote WWDC 2018</cite>
</div>

<!-- ![image](/assets/img/AR-QL-Pictures/Screenshot1.png) -->

<a rel="ar" href="/assets/img/AR-QL-Pictures/retrotv.usdz">
    <img src="/assets/img/AR-QL-Pictures/Screenshot5.jpg">
</a>

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

### Creating 3D Models for AR Quick Look

![image](/assets/img/AR-QL-Pictures/Screenshot5.jpg)

When we're creating our models, there are six things we need to get right:  
We need to set the model's placement, we need to set its physical size to be correct in AR, we need to create any animation we want for our model, add its contact shadow, modify its appearance, and then add any transparency that our model needs.  
Once these six things are done, we can optimize and export our models for use in AR Quick Look.  

###### Placement:  
The object should face toward the camera, toward positive z.  
The base of the object should sit on the ground plane, the plane where y = 0.  
We should put its natural pivot point at the origin.  

![image](/assets/img/AR-QL-Pictures/Screenshot4.jpg)

When you're thinking how to position your objects for this optimal recognition, think how you would place that object if you put it on a shelf or in a display cabinet.  
Now, this profile really matters.
Not only is it what people will see when your object first loads in our Quick Look, but it's also the profile that's used for the object's thumbnail, and these two deliberately match when the thumbnail is in files or in messages.  
So, we get that seamless transition between the two.  

###### Physical size

The second thing we want to set up for our model is its physical size.  
(not all objects have a natural size.)  

###### Animations.   
We recommend you use where it helps to bring that object to life with an idle animation that makes it feel more like it's in the world.  Note that animations always loop, and the animations you could create can use skeletal and/or transform animation to bring them to life.

###### Contact shadow
Another thing that really brings your models to life in the world is that contact shadow.  
Now, note here that AR Quick Look provides the contact shadow for you.  
This means that it can turn the shadow on and off as you transition between modes.  
It also means it can apply ambient lighting conditions to the shadow as the lighting changes around you.  
Because of this, don't bake a contact shadow into the models you provide.
If you do, you'll end up with two shadows.  
Note also that the first frame of any animation is used to create the shadow for a model, and sometimes this means it's important to choose the right first frame.  

###### Appearance

AR Quick Look uses a `Physically Based Rendering`, or `PBR shader`, and this gives us another six things that we can modify about our model's appearance to make it feel more real in the world.  

- Albedo (base color). This is the base color of the model, its underlying color. Should be RGB, or RBGA, if you're also providing transparency 
- Metallic (conductor or insulator). It is indicating which parts of the model are metallic. This changes whether they are a conductor or an insulator, which changes how they interact with the physics of light in the real world. (should be Greyscale)  
- Roughness (rough or shiny). We could also specify which parts of our model are rough or shiny by providing a roughness texture.(should be Greyscale)  
- Normal (surface details). We can add in a `normal map`. This creates the illusion of depth and variances within the surfaces, the model's surface, without changing the underlying mesh.(Should be RGB)  
- Ambient occlusion (internal shadows) We can add an ambient occlusion texture to specify where the model casts shadows on itself in the crevices and nooks and crannies of the model.(should be Greyscale)  
- Emissive (emits light). And if our model emits lights, we can provide an emissive texture for things like a TV screen or a computer monitor.(Should be RGB)  

The textures should be square. They should be powers of 2 squared. So, 2048, 1024, 512 pixels, so on.  

Optimize and test your models for high-memory devices iPhone 7 Plus, iPhone 8 Plus, iPhone X iPad Pro 12.9”.  
AR Quick Look will dynamically downsample textures for other devices when needed.  
Meshes and animations are not modified.  


###### Transparency

We can also make parts of our models transparent.  
This is useful for making objects made out of partly glass, for example.  
If you do this, be sure to use a separate material for the transparent and non-transparent parts of your model to ensure they render correctly.  
You do this by providing an albedo texture that has the transparency in its alpha channel.  
Note that transparency is really intended for see-through parts of the model, not for creating cutouts like a leaf edge or a butterfly wing.  


### The USDZ format

![image](/assets/img/AR-QL-Pictures/ARKit-Badge.pdf)

Sharing a 3D model between all these apps requires the models to be bundled up in a single sharable file.  

To enable this, AR Quick Look supports `usdz`, which is a new file format for mobile distribution of 3D models.  
`usdz` packages all these models and textures into a single file for efficient delivery of 3D content without having to work with reference files.  
It's based on Pixar's open-source `Universal Scene Description` format, or short, `USD`.  


#### How to convert 3D models into the usdz format using the new usdz Converter tool in Xcode 10.

This is a command line tool that will convert existing 3D models to usdz format.  
It ships inside Xcode 10, and in addition to creating usdz files, you could also use it to map PBR textures to the meshes and submeshes inside those existing models.  
It takes three input formats: OBJ files, Alembic files, or existing USD files, either USDA or USDC, the ASCII and binary versions of USD.

We call the tool with `xcrun` because it ships inside Xcode.  

If you get this error message:
`xcrun: error: unable to find utility "usdz_converter", not a developer tool or in PATH`
then you need to open Xcode preferences and select the commandline tools from location as below

![image](/assets/img/AR-QL-Pictures/Screenshot6.jpg)


We pass in the name of the model we want to convert, an OBJ file in this case, and the file name of the usdz we want to have the other end.  
To map PBR textures to the meshes they're in, we use the -g option, followed by the name of one of the groups, a mesh or a submesh that we want to map them to, and then we can provide any number of these textures for that particular group.  
You can pass in the -v option for verbose output.  
This will print the names of the groups that we find in the model plus useful other information about the conversion process.  

{% highlight swift %}
// Call usdz_converter with xcrun.
xcrun usdz_converter RetroTV.obj RetroTV.usdz
 
// PBR textures can be applied to groups (meshes and submeshes) with the -g option.
xcrun usdz_converter RetroTV.obj RetroTV.usdz
 -g RetroTVMesh
 -color_map RetroTV_Albedo.png
 -metallic_map RetroTV_Metallic.png
 -roughness_map RetroTV_Roughness.png
 -normal_map RetroTV_Normal.png
 -ao_map RetroTV_AmbientOcclusion.png
 -emissive_map RetroTV_Emissive.png

// Use the -v option to print out group names and other verbose information during conversion.
xcrun usdz_converter RetroTV.obj RetroTV.usdz -v

{% endhighlight %}
 
###### Let's look inside a usdz file.
In essence, these are uncompressed zip archives. The first file is always a usdc file.  
This contains the model's mesh, its animation, if it has some, and any material definitions it needs.  
And then, the remainder of the files in the archive are any textures, any images, like the ones we saw earlier on.   
This is an open format and Pixar have published the direct specification for usdz.   
 
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


### Sources:

https://developer.apple.com/videos/play/wwdc2018/603/

https://forums.developer.apple.com/thread/104042

https://developer.apple.com/videos/play/wwdc2018/237/

https://developer.apple.com/videos/play/wwdc2018/805/

<hr>

[^1]: What are MIME types? MIME types describe the media type of content either in email or served by web servers or web applications and are intended to help guide a web browser in how the content is to be processed and displayed. Examples of MIME types are: text/html for normal web pages, text/plain for plain text. To define a new MIME type you should add the following line in a file named `.htaccess` in the folder where the files for your website reside for ex: `AddType TYPE .extension`
