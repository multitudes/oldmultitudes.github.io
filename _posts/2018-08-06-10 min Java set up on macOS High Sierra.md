---
layout: post
title: Ten minutes Java set up on macOS High Sierra
date : 2018-08-06
published: true
---

#### Open the currect perspective (view).
If you're not already in the Java perspective, in the main 
menu select 
Window> Open Perspective > Java 

![screenshot1](/assets/img/java/ScreenShot1.png){:class="img-responsive"}

#### Create a Java Project
Before creating a class, we need a project to put it in. In the main toolbar, click on the New Java Project button, or click on the link below. Enter "HelloWorld" for the project name, then click Finish

#### Create the class
The next step is to create a new class. In the main toolbar again, click on the "New Java Class" button (or the link below). If not already specified, select 'HelloWorld/src' as the source folder. Enter HelloWorld for the class name, select the checkbox to create the main() method, then click Finish.
The Java editor will automatically open showing your new class.

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