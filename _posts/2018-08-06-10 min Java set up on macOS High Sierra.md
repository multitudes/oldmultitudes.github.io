---
layout: post
title: Ten minutes Java set up on macOS High Sierra
date : 2018-08-06
published: true
---
<div class="message">
First time Java with no problems. Install and test the development environment
</div>
To start with Java on your mac strt with download the [JDK](https://www.oracle.com/technetwork/java/javase/downloads/jdk11-downloads-5066655.html)
Download the [Eclipse IDE](https://www.eclipse.org/downloads/download.php?file=/oomph/epp/2018-12/R/eclipse-inst-mac64.dmg&mirror_id=518)

Open eclipse

#### Open the currect perspective (view).
<!--excerpt.start-->

![screenshot1](/assets/img/java/ScreenShot1.png){:class="img-responsive"}
If you're not already in the Java perspective, in the main 
menu select 
Window> Open Perspective > Java

<!--excerpt.end-->

#### Create a Java Project
Before creating a class, we need a project to put it in. In the main toolbar, click on the New Java Project button, or click on the link below. Enter "HelloWorld" for the project name, then click 'Finish'

![screenshot2](/assets/img/java/ScreenShot2.png){:class="img-responsive"}

#### Create the class
The next step is to create a new class. In the main toolbar again, click on the "New Java Class" button (or the link below). If not already specified, select 'HelloWorld/src' as the source folder. Enter HelloWorld for the class name, select the checkbox to create the main() method, then click Finish.
The Java editor will automatically open showing your new class.

![screenshot3](/assets/img/java/ScreenShot3.png){:class="img-responsive"}

#### Add a print statement
Now that you have your HelloWorld class, in the main() method, add the following statement:
{% highlight java %}
System.out.println("Hello world!");
{% endhighlight %}
Then save your changes; the class will automatically compile 
upon saving.

#### Run the application
To run your application, right-click on your class in the Package Explorer and select Run As > Java Application or press command-fn-f11 on a mac notebook. 
The Console view should appear at the bottom and display the "Hello, world!" output.

![screenshot4](/assets/img/java/ScreenShot4.png){:class="img-responsive"}